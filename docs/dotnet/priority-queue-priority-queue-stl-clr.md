---
title: priority_queue::priority_queue (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue member [STL/CLR]
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cb50eed9dbfcbe9480a6588ff10f966f1888205
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163391"
---
# <a name="priorityqueuepriorityqueue-stlclr"></a>priority_queue::priority_queue (STL/CLR)
Construit un objet d’adaptateur de conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### <a name="parameters"></a>Paramètres  
 suite  
 Conteneur à copier.  
  
 premier  
 Début de la plage à insérer.  
  
 last  
 Fin de la plage à insérer.  
  
 pred  
 Classement de prédicat pour la séquence contrôlée.  
  
 droite  
 Objet ou plage à insérer.  
  
## <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `priority_queue();`  
  
 Crée un conteneur vide encapsulé, avec la valeur par défaut de classement de prédicat. Il permet de spécifier une séquence contrôlée initiale vide avec la valeur par défaut de classement de prédicat.  
  
 Le constructeur :  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 Crée un conteneur encapsulé est une copie de `right.get_container()`, avec le prédicat de tri `right.value_comp()`. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `right`, avec le même classement.  
  
 Le constructeur :  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 Crée un conteneur encapsulé est une copie de `right->get_container()`, avec le prédicat de tri `right->value_comp()`. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `*right`, avec le même classement.  
  
 Le constructeur :  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri `pred`. Il permet de spécifier une séquence contrôlée initiale vide avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri `pred`, puis transmet tous les éléments de `cont` il permet de spécifier une séquence contrôlée initiale à partir d’un conteneur existant, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri par défaut, puis exécute un push de la séquence [`first`, `last`). Il permet de spécifier une séquence contrôlée initiale à partir d’un eqeuence spécifié, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri `pred`, puis exécute un push de la séquence [`first`, `last`). Il permet de spécifier une séquence contrôlée initiale à partir d’un seqeuence spécifié, avec le prédicat de tri spécifié.  
  
 Le constructeur :  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 Crée un conteneur vide encapsulé, avec le prédicat de tri `pred`, puis transmet tous les éléments de `cont` ainsi que la séquence [`first`, `last`). Il permet de spécifier une séquence contrôlée initiale à partir d’un conteneur existant et un seqeuence spécifié, avec le prédicat de tri spécifié.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::Assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)