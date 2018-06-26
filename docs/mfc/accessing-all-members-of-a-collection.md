---
title: L’accès à tous les membres d’une Collection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf25b84c4ee9808210d2dbf2f5115319a517c71b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931936"
---
# <a name="accessing-all-members-of-a-collection"></a>Accès à tous les membres d'une collection
Les classes de collection de tableau MFC (qu’elles soient ou non basées sur un modèle) utilisent des index pour accéder à leurs éléments. Les classes de collection de mappage et de liste MFC (qu’elles soient ou non basées sur un modèle) utilisent un indicateur de type **POSITION** pour décrire une position donnée dans la collection. Pour accéder à un ou plusieurs membres d’une collection de ce type, vous devez en premier lieu initialiser l’indicateur de position et passer plusieurs fois cette position à la collection et lui demander de retourner l’élément suivant. La collection n’est pas responsable du suivi des informations d’état de la progression de l’itération. Ces informations sont conservées dans l’indicateur de position. En revanche, pour une position donnée, la collection est chargée de retourner l’élément suivant.  
  
 Les procédures suivantes montrent comment itérer sur les trois principaux types de collection fournis avec MFC :  
  
-   [Itération d’un tableau](#_core_to_iterate_an_array)  
  
-   [Itération d’une liste](#_core_to_iterate_a_list)  
  
-   [Itération d’un mappage](#_core_to_iterate_a_map)  
  
### <a name="_core_to_iterate_an_array"></a> Pour itérer un tableau  
  
1.  Utilisez des numéros d’index séquentiels avec la fonction membre `GetAt` :  
  
     [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]  
  
     Cet exemple utilise un tableau de pointeurs typés qui contient des pointeurs vers des objets `CPerson` . Le tableau est dérivé de la classe `CObArray`, l’une des classes prédéfinies non basées sur un modèle. `GetAt` retourne un pointeur vers un objet `CPerson` . Pour les classes de collection de pointeurs typés (tableaux ou listes), le premier paramètre spécifie la classe de base ; le deuxième paramètre spécifie le type à stocker.  
  
     Le `CTypedPtrArray` classe également des surcharges de la **[]** opérateur afin que vous pouvez utiliser la syntaxe tableau-indice habituel pour accéder aux éléments d’un tableau. Une alternative à l’instruction dans le corps de la **pour** boucle  
  
     [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]  
  
     Cet opérateur existe dans les versions **const** et non**const** . La version **const** , qui est appelée pour les tableaux **const** , peuvent apparaître uniquement à droite d’une instruction d’assignation.  
  
### <a name="_core_to_iterate_a_list"></a> Pour itérer une liste  
  
1.  Utilisez les fonctions membres `GetHeadPosition` et `GetNext` pour parcourir la liste :  
  
     [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]  
  
     Cet exemple utilise une liste de pointeurs typés destinée à contenir des pointeurs vers des objets `CPerson` . La déclaration de liste ressemble à celle du tableau de la procédure [Pour itérer un tableau](#_core_to_iterate_an_array) , sauf qu’elle est dérivée de la classe `CObList`. `GetNext` retourne un pointeur vers un objet `CPerson` .  
  
### <a name="_core_to_iterate_a_map"></a> Pour itérer un mappage  
  
1.  Utilisez `GetStartPosition` pour atteindre le début du mappage et `GetNextAssoc` pour obtenir plusieurs fois la clé et la valeur suivantes du mappage, comme le montre l’exemple suivant :  
  
     [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]  
  
     Cet exemple utilise un modèle de mappage simple (et non une collection de pointeurs typés) qui utilise des clés `CString` et stocke des pointeurs vers des objets `CPerson` . Quand vous utilisez des fonctions d’accès, telles que `GetNextAssoc`, la classe fournit des pointeurs vers des objets `CPerson` . Si, à la place, vous utilisez l’une des collections de mappages non basés sur un modèle, vous devez convertir le pointeur `CObject` retourné en pointeur vers un `CPerson`.  
  
    > [!NOTE]
    >  Pour les mappages non basés sur un modèle, le compilateur nécessite une référence à un pointeur `CObject` dans le dernier paramètre de `GetNextAssoc`. En entrée, vous devez convertir vos pointeurs dans ce type, comme le montre l’exemple suivant.  
  
     La solution avec modèle est plus simple et assure une meilleure sécurité de type. Le code sans modèle est plus compliqué, comme vous pouvez le constater ici :  
  
     [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]  
  
 Pour plus d’informations, consultez [Suppression de tous les objets d’une collection CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Collections](../mfc/collections.md)

