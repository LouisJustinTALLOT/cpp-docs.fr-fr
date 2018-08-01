---
title: 'Comment : créer et utiliser des Instances unique_ptr | Microsoft Docs'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eed34b3c356b36c824e22739697b7967575792f6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402648"
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>Comment : créer et utiliser des instances unique_ptr
Un [unique_ptr](../standard-library/unique-ptr-class.md) ne partage pas son pointeur. Il ne peut pas être copié vers un autre `unique_ptr`, passé par valeur à une fonction ou utilisés dans n’importe quel algorithme de bibliothèque C++ Standard qui nécessite des clichés. Un `unique_ptr` peut uniquement être déplacé. Cela signifie que la propriété de la ressource mémoire est transférée à un autre `unique_ptr` et que le `unique_ptr` d'origine ne le possède plus. Il est recommandé de restreindre un objet à un seul propriétaire, car la multiplicité des propriétaires ajoute de la complexité à la logique du programme. Par conséquent, lorsque vous avez besoin d’un pointeur intelligent pour un objet ordinaire C++, utilisez `unique_ptr`, et lorsque vous construisez un `unique_ptr`, utilisez le [make_unique](../standard-library/memory-functions.md#make_unique) fonction d’assistance.  
  
 Le diagramme suivant illustre le transfert de propriété entre deux instances `unique_ptr`.  
  
 ![Déplacement de la propriété d’un unique&#95;ptr](../cpp/media/unique_ptr.png "unique_ptr")  
  
 `unique_ptr` est défini dans le `<memory>` en-tête dans la bibliothèque Standard C++. Il est exactement aussi efficace que d’un pointeur brut et peut être utilisé dans des conteneurs de bibliothèque C++ Standard. L’ajout de `unique_ptr` instances aux conteneurs de bibliothèque Standard C++ est efficace, car le constructeur de déplacement de la `unique_ptr` élimine la nécessité d’une opération de copie.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer des instances `unique_ptr` et les passer entre des fonctions.  
  
 [!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]  
  
 Ces exemples illustrent cette caractéristique de base de `unique_ptr` : il peut être déplacé, mais pas copié. Le « déplacement » transfère la propriété à un nouvel `unique_ptr` et réinitialise l'ancien `unique_ptr`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer des instances `unique_ptr` et les utiliser dans un vecteur.  
  
 [!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]  
  
 Dans la boucle for de plage, remarquez que `unique_ptr` est passé par référence. Si vous essayez d'effectuer un passage par valeur ici, le compilateur génère une erreur, car le constructeur de copie `unique_ptr` est supprimé.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment initialiser un `unique_ptr` qui est un membre de classe.  
  
 [!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez utiliser [make_unique](../standard-library/memory-functions.md#make_unique) pour créer un `unique_ptr` dans un tableau, mais vous ne pouvez pas utiliser `make_unique` pour initialiser les éléments du tableau.  
  
 [!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]  
  
 Pour plus d’exemples, consultez [make_unique](../standard-library/memory-functions.md#make_unique).  
  
## <a name="see-also"></a>Voir aussi  
 [Pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md)   
 [make_unique](../standard-library/memory-functions.md#make_unique)