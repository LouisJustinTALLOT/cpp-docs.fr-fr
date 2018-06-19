---
title: Queue::Queue (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::queue
dev_langs:
- C++
helpviewer_keywords:
- queue member [STL/CLR]
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eb556a4df1c8ce52c54f0cd249be71d0ea9019bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161400"
---
# <a name="queuequeue-stlclr"></a>queue::queue (STL/CLR)
Construit un objet d’adaptateur de conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>Paramètres  
 droite  
 Objet à copier.  
  
 encapsulé  
 Conteneur encapsulée à utiliser.  
  
## <a name="remarks"></a>Notes  
 Le constructeur :  
  
 `queue();`  
  
 Crée un conteneur encapsulé vide. Il permet de spécifier une séquence contrôlée initiale vide.  
  
 Le constructeur :  
  
 `queue(queue<Value, Container>% right);`  
  
 Crée un conteneur encapsulé est une copie de `right.get_container()`. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `right`.  
  
 Le constructeur :  
  
 `queue(queue<Value, Container>^ right);`  
  
 Crée un conteneur encapsulé est une copie de `right->get_container()`. Il permet de spécifier une séquence contrôlée initiale qui est une copie de la séquence contrôlée par l’objet de file d’attente `*right`.  
  
 Le constructeur :  
  
 `explicit queue(container_type wrapped);`  
  
 utilise le conteneur existant `wrapped` comme conteneur encapsulé. Il permet de construire une file d’attente à partir d’un conteneur existant.  
  
## <a name="example"></a>Exemple  
  
```  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::Assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)   
 [Queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)