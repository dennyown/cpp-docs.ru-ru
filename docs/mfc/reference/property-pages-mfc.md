---
title: "Страницы свойств (MFC) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages, global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 50888697fe01d3a84d9aa4c6f5f92926e4681535
ms.lasthandoff: 02/24/2017

---
# <a name="property-pages-mfc"></a>Страницы свойств (MFC)
Страницы свойств отображения текущих значений свойств элемента управления OLE в настраиваемый графический интерфейс для просмотра и редактирования, поддерживая механизм сопоставления данных, основанный на обмен данными (диалоговых окон DDX).  
  
 Этот механизм сопоставления данных сопоставляет элементы управления страницы свойств отдельные свойства элемента управления OLE. Значение свойства элемента управления отражает состояние или содержимое элемента управления страницы свойств. Сопоставление элементов управления страницы свойств и свойств определяется **DDP_** вызывает функцию на странице свойств `DoDataExchange` функции-члена. Ниже приведен список **DDP_** функций, которые обмениваются данные, введенные с помощью страницы свойств элемента управления:  
  
### <a name="property-page-data-transfer"></a>Передача данных страницы свойств  
  
|||  
|-|-|  
|[DDP_CBIndex](#ddp_cbindex)|Связывает индекс выбранной строки в поле со списком со свойством элемента управления.|  
|[DDP_CBString](#ddp_cbstring)|Связывает выбранную строку в поле со списком со свойством элемента управления. Можно начать с того же буквы как значение свойства выбранной строки, но не требуется полностью совпадают.|  
|[DDP_CBStringExact](#ddp_cbstringexact)|Связывает выбранную строку в поле со списком со свойством элемента управления. Выбранной строки и значения свойства строки должны точно совпадать.|  
|[DDP_Check](#ddp_check)|Связывает флажок на странице свойств элемента управления со свойством элемента управления.|  
|[DDP_LBIndex](#ddp_lbindex)|Связывает индекс выбранной строки в поле со списком со свойством элемента управления.|  
|[DDP_LBString](#ddp_lbstring)|Связывает выбранную строку в поле со списком со свойством элемента управления. Можно начать с того же буквы как значение свойства выбранной строки, но не должно соответствовать его полностью.|  
|[DDP_LBStringExact](#ddp_lbstringexact)|Связывает выбранную строку в поле со списком со свойством элемента управления. Выбранной строки и значения свойства строки должны точно совпадать.|  
|[DDP_PostProcessing](#ddp_postprocessing)|Завершает передачу значения свойств из элемента управления.|  
|[DDP_Radio](#ddp_radio)|Ссылки в переключателе на странице свойств элемента управления со свойством элемента управления.|  
|[DDP_Text](#ddp_text)|Элемент управления на странице свойств элемента управления со свойством элемента управления ссылками. Эта функция обрабатывает несколько различных типов свойств, таких как **двойные**, **короткие**, `BSTR`, и **длинные**.|  
  
 Дополнительные сведения о `DoDataExchange` страницы функций и свойств, см. в статье [элементы управления ActiveX: страницы свойств](../../mfc/mfc-activex-controls-property-pages.md).  
  
 Ниже приведен список макросов, которые используются для создания и управления страниц свойств для элемента управления OLE.  
  
### <a name="property-pages"></a>Страницы свойств  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Начинает список кодов страницы свойств.|  
|[END_PROPPAGEIDS](#end_proppageids)|Завершает список кодов страницы свойств.|  
|[PROPPAGEID](#proppageid)|Объявляет страницы свойств класса элемента управления.|  
  
##  <a name="a-nameddpcbindexa--ddpcbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации с индекс текущего выделенного фрагмента в поле со списком на странице свойств значение свойства целого числа.  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в поле со списком поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена со списком, определяемое `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_CBIndex` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddpcbstringa--ddpcbstring"></a><a name="ddp_cbstring"></a>DDP_CBString  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации с текущее выделение в поле со списком на странице свойств значение строкового свойства.  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в поле со списком поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на строки поле со списком, заданной параметром `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_CBString` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddpcbstringexacta--ddpcbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации значение строковое свойство, точно соответствует текущее выделение в поле со списком на странице свойств.  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в поле со списком поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на строки поле со списком, заданной параметром `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_CBStringExact` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddpchecka--ddpcheck"></a><a name="ddp_check"></a>DDP_Check  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации с управления "флажок" для связанного свойства страницы значение свойства.  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса для управления "флажок", связанный со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на элемент управления флажком, определяемое `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_Check` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddplbindexa--ddplbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации с индекс текущего выделенного фрагмента в списке на странице свойств значение свойства целого числа.  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в списке поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на список поле строки `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_LBIndex` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddplbstringa--ddplbstring"></a><a name="ddp_lbstring"></a>DDP_LBString  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации с текущее выделение в списке на странице свойств значение строкового свойства.  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в списке поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на список поле строки `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_LBString` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddplbstringexacta--ddplbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact  
 Эта функция вызывается на странице свойств `DoDataExchange` функции для синхронизации значение строковое свойство, точно соответствует текущее выделение в списке на странице свойств.  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса в списке поле элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена на список поле строки `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_LBStringExact` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddppostprocessinga--ddppostprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing  
 Эта функция вызывается на странице свойств `DoDataExchange` функция завершения передачи значений свойств на странице свойств для элемента управления при сохранении значений свойств.  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
### <a name="remarks"></a>Примечания  
 Эту функцию следует вызывать после завершения все функции обмена данными. Пример:  
  
 [!code-cpp[NVC_MFCAxCtl&#15;](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddpradioa--ddpradio"></a><a name="ddp_radio"></a>DDP_Radio  
 Эта функция вызывается в элементе управления `DoPropExchange` функции для синхронизации с связанного свойства страницы переключателя значение свойства.  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса радио кнопки элемента управления, связанного со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена с помощью переключателя, определяемое `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_Radio` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameddptexta--ddptext"></a><a name="ddp_text"></a>DDP_Text  
 Эта функция вызывается в элементе управления `DoDataExchange` функция синхронизации значение свойства с связанного свойства элемента управления страницы.  
  
```   
void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    BYTE & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    UINT & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    long & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    DWORD & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    float & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    double & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    CString & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Параметры  
 `pDX`  
 Указатель на `CDataExchange` объект. Структура предоставляет этот объект для формирования контекста обмена данными, включая его направление.  
  
 `id`  
 Идентификатор ресурса для элемента управления, связанный со свойством элемента управления `pszPropName`.  
  
 `member`  
 Связанные с управления страницы свойств, указанный в переменной-члена `id` и свойство, заданное параметром `pszPropName`.  
  
 `pszPropName`  
 Имя свойства для свойства элемента управления для обмена с элементом управления, заданные `id`.  
  
### <a name="remarks"></a>Примечания  
 Эта функция должна вызываться до соответствующей `DDX_Text` вызов функции.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-namebeginproppageidsa--beginproppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS  
 Начинается определение списка элемента управления на странице свойств идентификаторов.  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>Параметры  
 *class_name*  
 Имя класса элемента управления, какие свойства указаны страницы.  
  
 *count*  
 Количество страниц свойств, используемых класс элемента управления.  
  
### <a name="remarks"></a>Примечания  
 В файле реализации (CPP), который определяет функции-члены класса, маркированный список свойств страницы с `BEGIN_PROPPAGEIDS` макрос, затем добавить макрос записи для каждой из страниц свойств и полный список страниц свойств с `END_PROPPAGEIDS` макрос.  
  
 Дополнительные сведения на страницах свойств см. в статье [элементы управления ActiveX: страницы свойств](../../mfc/mfc-activex-controls-property-pages.md).  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameendproppageidsa--endproppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS  
 Завершает определение списка идентификатор страницы свойств.  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>Параметры  
 *class_name*  
 Имя класса элемента управления, которому принадлежит страница свойств.  
  
### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
  
##  <a name="a-nameproppageida--proppageid"></a><a name="proppageid"></a>PROPPAGEID  
 Добавляет страницы свойств для использования элемента управления OLE.  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>Параметры  
 `clsid`  
 Идентификатор уникального класса страницы свойств.  
  
### <a name="remarks"></a>Примечания  
 Все `PROPPAGEID` макросы должны быть помещены между `BEGIN_PROPPAGEIDS` и `END_PROPPAGEIDS` макросы в файле реализации элемента управления.  

### <a name="requirements"></a>Требования  
  **Заголовок** afxctl.h  
    
## <a name="see-also"></a>См. также  
 [Макросы и глобальные объекты](../../mfc/reference/mfc-macros-and-globals.md)
