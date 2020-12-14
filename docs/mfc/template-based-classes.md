---
description: 'En savoir plus sur : classes Template-Based'
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
ms.openlocfilehash: 87b03c649bfb6acf401c3ee78e6db07c1185dff5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216312"
---
# <a name="template-based-classes"></a>Classes basées sur un modèle

Cet article explique les classes de collection basées sur un modèle de type sécurisé dans MFC 3.0 et les versions ultérieures. L'utilisation de ces modèles pour créer des collections de type sécurisé est une solution plus pratique qui offre une plus grande cohérence des types que les classes de collection qui ne sont pas basées sur des modèles.

MFC prédéfinit deux catégories de collections basées sur des modèles :

- [Classes de tableau, de liste et de table simples](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tableaux, listes et tables de pointeurs typés](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Toutes les classes de collection simples sont dérivées de la classe `CObject`, de sorte qu'elles héritent de la sérialisation, de la création dynamique et d'autres propriétés de `CObject`. Les classes de collection de pointeurs typés nécessitent que vous spécifiez la classe de dérivation, qui doit être l’une des collections de pointeurs non basées sur un modèle prédéfinies par MFC, par exemple `CPtrList` ou `CPtrArray`. La nouvelle classe de collection hérite de la classe de base spécifiée, et ses fonctions membres utilisent des appels encapsulés aux membres de la classe de base pour appliquer la cohérence des types.

Pour plus d’informations sur les modèles C++, consultez [modèles](../cpp/templates-cpp.md) dans la *Référence du langage c++*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> Utilisation de modèles de tableau, de liste et de carte simples

Pour utiliser les modèles de collection simples, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a> Utilisation simple des tableaux et des listes

Les classes de tableau et de liste simples, [CArray](../mfc/reference/carray-class.md) et [CList](../mfc/reference/clist-class.md), acceptent deux paramètres : *type* et `ARG_TYPE` . Ces classes peuvent stocker n’importe quel type de données, que vous spécifiez dans le paramètre de *type* :

- Types de données C++ fondamentaux, tels que **`int`** , **`char`** et **`float`**

- Structures et classes C++

- Autres types que vous définissez

Pour plus de commodité et d’efficacité, vous pouvez utiliser le paramètre *arg_type* pour spécifier le type d’arguments de fonction. En général, vous spécifiez *arg_type* comme une référence au type que vous avez nommé dans le paramètre de *type* . Par exemple :

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Le premier exemple déclare une collection de tableaux, `myArray` , qui contient des **`int`** . Le deuxième exemple déclare une collection de listes, `myList`, qui stocke des objets `CPerson`. Certaines fonctions membres des classes de collection acceptent des arguments dont le type est spécifié par le paramètre de modèle *arg_type* . Par exemple, la `Add` fonction membre de la classe `CArray` prend un argument *arg_type* :

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a> Utilisation de mappage simple

La classe de mappage simple, [CMAP](../mfc/reference/cmap-class.md), prend quatre paramètres *: Key*, *ARG_KEY*, *value* et *ARG_VALUE*. À l'instar des classes de tableau et de liste, les classes de table peuvent stocker n'importe quel type de données. Contrairement aux tableaux et listes, qui indexent et classent les données qu'ils contiennent, les tables associent des clés et des valeurs. Vous accédez à une valeur stockée dans une table en spécifiant la clé qui lui est associée. Le paramètre de *clé* spécifie le type de données des clés utilisées pour accéder aux données stockées dans la carte. Si le type de *clé* est une structure ou une classe, le paramètre *ARG_KEY* est généralement une référence au type spécifié dans la *clé*. Le paramètre *value* spécifie le type des éléments stockés dans la classe Map. Si le type de *ARG_VALUE* est une structure ou une classe, le paramètre *ARG_VALUE* est généralement une référence au type spécifié dans *valeur*. Par exemple :

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Le premier exemple stocke des `MY_STRUCT` valeurs, y accède par des **`int`** clés et retourne des `MY_STRUCT` éléments accessibles par référence. Le deuxième exemple stocke des valeurs `CPerson`, y accède par des clés `CString` et retourne les références aux éléments accédés. Cet exemple peut représenter un carnet d'adresses simple où vous recherchez des personnes par leur nom de famille.

Étant donné que le paramètre de *clé* est de type `CString` et que le paramètre *KEY_TYPE* est de type `LPCSTR` , les clés sont stockées dans la classe Map en tant qu’éléments de type, `CString` mais elles sont référencées dans des fonctions telles que `SetAt` des pointeurs de type `LPCSTR` . Par exemple :

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a> Utilisation de modèles de collection Typed-Pointer

Pour utiliser les modèles de collection de pointeurs typés, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a> Typed-Pointer l’utilisation des tableaux et des listes

Les classes de tableau et de liste de pointeurs typés, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) et [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), acceptent deux paramètres : *BASE_CLASS* et *type*. Ces classes peuvent stocker n’importe quel type de données, que vous spécifiez dans le paramètre de *type* . Elles sont dérivées de l’une des classes de collection non basées sur des modèles qui stockent des pointeurs ; vous spécifiez cette classe de base dans *BASE_CLASS*. Pour les tableaux, utilisez `CObArray` ou `CPtrArray`. Pour les listes, utilisez `CObList` ou `CPtrList`.

En effet, lorsque vous déclarez une collection basée sur `CObList`, non seulement la nouvelle classe hérite des membres de sa classe de base, mais elle déclare également plusieurs opérateurs et fonctions membres de type sécurisé qui aident à assurer la cohérence des types en encapsulant des appels aux membres de la classe de base. Ces encapsulations gèrent toutes les conversions de type nécessaires. Par exemple :

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Le premier exemple déclare un tableau de pointeurs typés, `myArray`, dérivé de `CObArray`. Le tableau stocke et retourne des pointeurs vers des objets `CPerson` (où `CPerson` est une classe dérivée de `CObject`). Vous pouvez appeler n’importe quelle `CObArray` fonction membre, ou vous pouvez appeler le nouveau type safe `GetAt` et les `ElementAt` fonctions ou utiliser l’opérateur de type sécurisé **[]** .

Le deuxième exemple déclare une liste de pointeurs typés, `myList`, dérivée de `CPtrList`. La liste stocke et retourne des pointeurs vers des objets `MY_STRUCT`. Une classe basée sur `CPtrList` est utilisée pour stocker des pointeurs vers des objets non dérivés de `CObject`. `CTypedPtrList` a plusieurs fonctions membres de type sécurisé : `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev` et `GetAt`.

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a> Utilisation de la carte de Typed-Pointer

La classe de mappage de pointeurs typés, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), prend trois paramètres : *BASE_CLASS*, *Key* et *value*. Le paramètre *BASE_CLASS* spécifie la classe à partir de laquelle dériver la nouvelle classe : `CMapPtrToWord` ,,,,, etc `CMapPtrToPtr` `CMapStringToPtr` `CMapWordToPtr` `CMapStringToOb` . La *clé* est analogue à la *clé* dans `CMap` : elle spécifie le type de la clé utilisée pour les recherches. La *valeur* est analogue à la *valeur* dans `CMap` : elle spécifie le type d’objet stocké dans la classe Map. Par exemple :

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Le premier exemple est un mappage basé sur `CMapPtrToPtr` : il utilise des `CString` clés mappées à des pointeurs vers `MY_STRUCT` . Vous pouvez rechercher un pointeur stocké en appelant une fonction membre de type sécurisé `Lookup`. Vous pouvez utiliser l’opérateur **[]** pour rechercher un pointeur stocké et l’ajouter s’il est introuvable. Vous pouvez également itérer la table à l'aide de la fonction de type sécurisé `GetNextAssoc`. Vous pouvez également appeler d'autres fonctions membres de la classe `CMapPtrToPtr`.

Le deuxième exemple est un mappage basé sur `CMapStringToOb` : il utilise des clés de chaîne mappées à des pointeurs stockés vers des `CMyObject` objets. Vous pouvez utiliser les mêmes membres de type sécurisé décrits dans le paragraphe précédent, ou vous pouvez appeler des membres de la classe `CMapStringToOb`.

> [!NOTE]
> Si vous spécifiez **`class`** un **`struct`** type ou pour le paramètre de *valeur* , au lieu d’un pointeur ou d’une référence au type, la classe ou la structure doit avoir un constructeur de copie.

Pour plus d’informations, consultez [comment créer un Type-Safe collection](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Voir aussi

[Regroupements](../mfc/collections.md)
