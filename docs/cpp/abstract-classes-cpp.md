---
title: "Абстрактные классы (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "абстрактные классы"
  - "базовые классы, абстрактные классы"
  - "классы [C++], абстрактный"
  - "производные классы, абстрактные классы"
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Абстрактные классы (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Абстрактные классы используются в качестве обобщенных концепций, на основе которых можно создавать более конкретные производные классы.  Невозможно создать объект типа абстрактного класса; однако можно использовать указатели и ссылки на типы абстрактного класса.  
  
 Класс, содержащий хотя бы одну чисто виртуальную функцию, считается абстрактным.  Классы, производные от абстрактного класса, должны реализовывать чисто виртуальную функцию; в противном случае они также будут абстрактными.  
  
 Виртуальная функция объявляется как "чистая" с помощью синтаксиса *спецификатора\-чистоты* \(рассмотренного в разделе [Реализация протокола класса](http://msdn.microsoft.com/ru-ru/a319f1b3-05e8-400e-950a-1ca6eb105ab5)\).  Рассмотрим пример, представленный в разделе [Виртуальные функции](../cpp/virtual-functions.md).  Класс `Account` создан для того, чтобы предоставлять общие функции, но объекты типа `Account` имеют слишком общий характер для практического применения.  Таким образом, класс `Account` является хорошим кандидатом в абстрактный класс:  
  
```  
// deriv_AbstractClasses.cpp  
// compile with: /LD  
class Account {  
public:  
   Account( double d );   // Constructor.  
   virtual double GetBalance();   // Obtain balance.  
   virtual void PrintBalance() = 0;   // Pure virtual function.  
private:  
    double _balance;  
};  
  
```  
  
 Единственное различие между этим и предыдущим объявлениями состоит в том, что функция `PrintBalance` объявлена со спецификатором чисто виртуальной функции pure \(`= 0`\).  
  
## Ограничения на использование абстрактных классов  
 Абстрактные классы невозможно использовать для следующих элементов:  
  
-   переменных и данных членов;  
  
-   типов аргументов;  
  
-   типов возвращаемых функциями значений;  
  
-   типов явных преобразований.  
  
 Другое ограничение состоит в том, что при вызове конструктором абстрактного класса чистой виртуальной функции \(прямо или косвенно\) результат будет неопределенным.  Однако конструкторы и деструкторы абстрактных классов могут вызывать другие функции\-члены.  
  
 Для абстрактных классов можно определять чистые виртуальные функции, но вызывать их можно только непосредственно с использованием следующего синтаксиса:  
  
 *имя\-абстрактного\-класса* `::` *имя\-функции***\( \)**  
  
 Это помогает при разработке иерархий классов, базовые классы которых содержат чистые виртуальные деструкторы, поскольку деструкторы базовых классов всегда вызываются в процессе удаления объекта.  Рассмотрим следующий пример.  
  
```  
// Declare an abstract base class with a pure virtual destructor.  
// deriv_RestrictionsonUsingAbstractClasses.cpp  
class base {  
public:  
    base() {}  
    virtual ~base()=0;  
};  
  
// Provide a definition for destructor.  
base::~base() {}  
  
class derived:public base {  
public:  
    derived() {}  
    ~derived(){}  
};  
  
int main() {  
    derived *pDerived = new derived;  
    delete pDerived;  
}  
```  
  
 При удалении объекта, указанного с помощью `pDerived`, сначала вызывается деструктор класса `derived`, а затем — деструктор класса `base`.  Пустая реализация чистой виртуальной функции гарантирует наличие хотя бы некоторой реализации для функции.  
  
> [!NOTE]
>  В предыдущем примере чистая виртуальная функция `base::~base` вызывается неявно из `derived::~derived`.  Чистые виртуальные функции можно также вызывать явно, используя полное имя функции\-члена.  
  
## См. также  
 [Наследование](../cpp/inheritance-cpp.md)