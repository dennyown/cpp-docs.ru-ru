---
title: "PTR::CreateInstance | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d764d18f3148dba663e1e6796c44a0add6aa8109
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
Создает экземпляр COM-объект внутри `com::ptr`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   System::String ^ progid  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   const wchar_t * progid  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   REFCLSID rclsid  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `progid`  
 Строка `ProgID`.  
  
 `pouter`  
 Указатель интерфейса IUnknown Агрегатный объект (управляющий IUnknown). Если `pouter` не указан, `NULL` используется.  
  
 `cls_context`  
 Контекст, в котором будет выполняться код, управляющий вновь созданный объект. Значения берутся из `CLSCTX` перечисления. Если `cls_context` не указан, значение, используемое CLSCTX_ALL.  
  
 `rclsid`  
 `CLSID`связанные с данными и код, который будет использоваться для создания объекта.  
  
## <a name="exceptions"></a>Исключения  
 Если `com::ptr` уже владеет ссылку на COM-объект `CreateInstance` вызывает <xref:System.InvalidOperationException>.  
  
 Эта функция вызывает `CoCreateInstance` и использует <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> преобразовать любой ошибки `HRESULT` в соответствующее исключение.  
  
## <a name="remarks"></a>Примечания  
 `CreateInstance`использует `CoCreateInstance` для создания нового экземпляра заданного объекта, определяемого с ProgID или CLSID. `com::ptr` Ссылается на вновь созданный объект и автоматически освобождает все принадлежащие ссылки после уничтожения.  
  
## <a name="example"></a>Пример  
 В этом примере реализуется класс CLR, который использует `com::ptr` программы-оболочки для своего закрытого члена `IXMLDOMDocument` объекта. Конструкторы класса использовать два разных вида `CreateInstance` для создания объекта документа от ProgID или CLSID, а также CLSCTX.  
  
```  
// comptr_createinstance.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
   XmlDocument(REFCLSID clsid, DWORD clsctx) {  
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc1("Msxml2.DOMDocument.3.0");  
  
      // or from a clsid with specific CLSCTX  
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
## <a name="requirements"></a>Требования  
 **Файл заголовка** \<msclr\com\ptr.h >  
  
 **Пространство имен** msclr::com  
  
## <a name="see-also"></a>См. также  
 [Члены ptr](../dotnet/ptr-members.md)