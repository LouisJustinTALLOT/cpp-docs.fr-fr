---
title: Classes basées sur un modèle
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 40633c8b2b09d27e97443364ed3ce711ee217e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306377"
---
# <a name="template-based-classes"></a>Classes basées sur un modèle

Cet article explique les classes de collection basées sur un modèle de type sécurisé dans MFC 3.0 et les versions ultérieures. L'utilisation de ces modèles pour créer des collections de type sécurisé est une solution plus pratique qui offre une plus grande cohérence des types que les classes de collection qui ne sont pas basées sur des modèles.

MFC prédéfinit deux catégories de collections basées sur des modèles :

- [Tableau simple, liste et classes de mappage](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tableaux, listes et tables de pointeurs typés](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Toutes les classes de collection simples sont dérivées de la classe `CObject`, de sorte qu'elles héritent de la sérialisation, de la création dynamique et d'autres propriétés de `CObject`. Les classes de collection de pointeurs typés nécessitent que vous spécifiez la classe de dérivation, qui doit être l’une des collections de pointeurs non basées sur un modèle prédéfinies par MFC, par exemple `CPtrList` ou `CPtrArray`. La nouvelle classe de collection hérite de la classe de base spécifiée, et ses fonctions membres utilisent des appels encapsulés aux membres de la classe de base pour appliquer la cohérence des types.

Pour plus d’informations sur les modèles C++, consultez [modèles](../cpp/templates-cpp.md) dans le *référence du langage C++*.

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> À l’aide de tableau Simple, liste et des modèles de la carte

Pour utiliser les modèles de collection simples, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

###  <a name="_core_simple_array_and_list_usage"></a> Tableau simple et liste

Les classes de liste et un tableau simple [CArray](../mfc/reference/carray-class.md) et [CList](../mfc/reference/clist-class.md), acceptent deux paramètres : *TYPE* et `ARG_TYPE`. Ces classes peuvent stocker n’importe quel type de données que vous spécifiez dans le *TYPE* paramètre :

- Types de données C++ fondamentaux, tels que **int**, **char**, et **float**

- Structures et classes C++

- Autres types que vous définissez

Pour plus de commodité et d’efficacité, vous pouvez utiliser la *ARG_TYPE* paramètre pour spécifier le type des arguments de fonction. En règle générale, vous spécifiez *ARG_TYPE* comme une référence au type nommé dans le *TYPE* paramètre. Exemple :

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Le premier exemple déclare une collection de tableaux, `myArray`, qui contient **int**s. Le deuxième exemple déclare une collection de listes, `myList`, qui stocke des objets `CPerson`. Certaines fonctions membres des classes de collection acceptent des arguments dont le type est spécifié par le *ARG_TYPE* paramètre de modèle. Par exemple, le `Add` fonction membre de classe `CArray` prend un *ARG_TYPE* argument :

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> Utilisation de tables simples

La classe de table simple, [CMap](../mfc/reference/cmap-class.md), accepte quatre paramètres : *CLÉ*, *ARG_KEY*, *valeur*, et *ARG_VALUE*. À l'instar des classes de tableau et de liste, les classes de table peuvent stocker n'importe quel type de données. Contrairement aux tableaux et listes qui indexent et classent les données stockées, les tables associent des clés et valeurs : Vous accéder à une valeur stockée dans une table en spécifiant la clé associée de la valeur. Le *clé* paramètre spécifie le type de données des clés utilisées pour accéder aux données stockées dans la table. Si le type de *clé* est une structure ou une classe, le *ARG_KEY* paramètre est généralement une référence au type spécifié dans *clé*. Le *valeur* paramètre spécifie le type des éléments stockés dans le mappage. Si le type de *ARG_VALUE* est une structure ou une classe, le *ARG_VALUE* paramètre est généralement une référence au type spécifié dans *valeur*. Exemple :

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Le premier exemple stocke `MY_STRUCT` valeurs, y accède par **int** clés et retourne accessibles `MY_STRUCT` éléments par référence. Le deuxième exemple stocke des valeurs `CPerson`, y accède par des clés `CString` et retourne les références aux éléments accédés. Cet exemple peut représenter un carnet d'adresses simple où vous recherchez des personnes par leur nom de famille.

Étant donné que le *clé* paramètre est de type `CString` et *KEY_TYPE* paramètre est de type `LPCSTR`, les clés sont stockées dans la carte en tant qu’éléments de type `CString` mais sont référencées dans les fonctions comme `SetAt` via des pointeurs de type `LPCSTR`. Exemple :

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> À l’aide de modèles de Collection de pointeurs typés

Pour utiliser les modèles de collection de pointeurs typés, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> Tableau de pointeurs typés et liste

Les classes de liste et un tableau de pointeurs typés [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) et [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), acceptent deux paramètres : *BASE_CLASS* et *TYPE*. Ces classes peuvent stocker n’importe quel type de données que vous spécifiez dans le *TYPE* paramètre. Ils sont dérivés de l’une des classes de collection basées sur des modèles qui stocke des pointeurs ; vous spécifiez cette classe de base dans *BASE_CLASS*. Pour les tableaux, utilisez `CObArray` ou `CPtrArray`. Pour les listes, utilisez `CObList` ou `CPtrList`.

En effet, lorsque vous déclarez une collection basée sur `CObList`, non seulement la nouvelle classe hérite des membres de sa classe de base, mais elle déclare également plusieurs opérateurs et fonctions membres de type sécurisé qui aident à assurer la cohérence des types en encapsulant des appels aux membres de la classe de base. Ces encapsulations gèrent toutes les conversions de type nécessaires. Exemple :

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Le premier exemple déclare un tableau de pointeurs typés, `myArray`, dérivé de `CObArray`. Le tableau stocke et retourne des pointeurs vers des objets `CPerson` (où `CPerson` est une classe dérivée de `CObject`). Vous pouvez appeler les `CObArray` fonction membre, ou vous pouvez appeler le nouveau type-safe `GetAt` et `ElementAt` les fonctions ou utiliser le type-safe **[]** opérateur.

Le deuxième exemple déclare une liste de pointeurs typés, `myList`, dérivée de `CPtrList`. La liste stocke et retourne des pointeurs vers des objets `MY_STRUCT`. Une classe basée sur `CPtrList` est utilisée pour stocker des pointeurs vers des objets non dérivés de `CObject`. `CTypedPtrList` a plusieurs fonctions membres de type sécurisé : `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev` et `GetAt`.

###  <a name="_core_typed.2d.pointer_map_usage"></a> Utilisation de tables de pointeurs typés

La classe de la table de pointeurs typés, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), accepte trois paramètres : *BASE_CLASS*, *clé*, et *valeur*. Le *BASE_CLASS* paramètre spécifie la classe à partir de laquelle dérive la nouvelle classe : `CMapPtrToWord`, `CMapPtrToPtr`, `CMapStringToPtr`, `CMapWordToPtr`, `CMapStringToOb`, et ainsi de suite. *CLÉ* est analogue à *clé* dans `CMap`: Elle spécifie le type de la clé utilisée pour les recherches. *VALEUR* est analogue à *valeur* dans `CMap`: Elle spécifie le type d’objet stocké dans la carte. Exemple :

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Le premier exemple est une table basée sur `CMapPtrToPtr` , elle utilise `CString` clés mappés vers des pointeurs en `MY_STRUCT`. Vous pouvez rechercher un pointeur stocké en appelant une fonction membre de type sécurisé `Lookup`. Vous pouvez utiliser la **[]** opérateur pour rechercher un pointeur stocké et l’ajouter s’il est introuvable. Vous pouvez également itérer la table à l'aide de la fonction de type sécurisé `GetNextAssoc`. Vous pouvez également appeler d'autres fonctions membres de la classe `CMapPtrToPtr`.

Le deuxième exemple est une table basée sur `CMapStringToOb` , il utilise des clés de chaîne mappées à des pointeurs vers `CMyObject` objets. Vous pouvez utiliser les mêmes membres de type sécurisé décrits dans le paragraphe précédent, ou vous pouvez appeler des membres de la classe `CMapStringToOb`.

> [!NOTE]
>  Si vous spécifiez un **classe** ou **struct** type pour le *valeur* paramètre, plutôt que d’un pointeur ou référence pour le type, la classe ou la structure doit avoir un constructeur de copie.

Pour plus d’informations, consultez [comment définir une Collection de Type sécurisé](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Voir aussi

[Collections](../mfc/collections.md)
