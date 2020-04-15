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
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370456"
---
# <a name="template-based-classes"></a>Classes basées sur un modèle

Cet article explique les classes de collection basées sur un modèle de type sécurisé dans MFC 3.0 et les versions ultérieures. L'utilisation de ces modèles pour créer des collections de type sécurisé est une solution plus pratique qui offre une plus grande cohérence des types que les classes de collection qui ne sont pas basées sur des modèles.

MFC prédéfinit deux catégories de collections basées sur des modèles :

- [Classes de tableau, de liste et de table simples](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [Tableaux, listes et tables de pointeurs typés](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

Toutes les classes de collection simples sont dérivées de la classe `CObject`, de sorte qu'elles héritent de la sérialisation, de la création dynamique et d'autres propriétés de `CObject`. Les classes de collection de pointeurs typés nécessitent que vous spécifiez la classe de dérivation, qui doit être l’une des collections de pointeurs non basées sur un modèle prédéfinies par MFC, par exemple `CPtrList` ou `CPtrArray`. La nouvelle classe de collection hérite de la classe de base spécifiée, et ses fonctions membres utilisent des appels encapsulés aux membres de la classe de base pour appliquer la cohérence des types.

Pour plus d’informations sur les modèles C, consultez [Templates](../cpp/templates-cpp.md) in the *CMD Language Reference*.

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>Utilisation de modèles simples de tableau, de liste et de carte

Pour utiliser les modèles de collection simples, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>Simple Array et Utilisation de la liste

Le tableau simple et les classes de liste, [CArray](../mfc/reference/carray-class.md) `ARG_TYPE`et [CList](../mfc/reference/clist-class.md), prendre deux paramètres: *TYPE* et . Ces classes peuvent stocker n’importe quel type de données, que vous spécifiez dans le paramètre *TYPE* :

- Types de données CMD fondamentaux, tels que **int,** **char,** et **float**

- Structures et classes C++

- Autres types que vous définissez

Pour plus de commodité et d’efficacité, vous pouvez utiliser le *paramètre ARG_TYPE* pour spécifier le type d’arguments de fonction. En règle générale, vous spécifiez *ARG_TYPE* en référence au type que vous avez nommé dans le paramètre *TYPE.* Par exemple :

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

Le premier exemple déclare une `myArray`collection de tableaux, , qui contient **int**s. Le deuxième exemple déclare une collection de listes, `myList`, qui stocke des objets `CPerson`. Certaines fonctions membres des classes de collection prennent des arguments dont le type est spécifié par le *paramètre ARG_TYPE* modèle. Par exemple, `Add` la fonction `CArray` de membre de la classe prend un *argument ARG_TYPE* :

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>Utilisation simple de carte

La classe de carte simple, [CMap](../mfc/reference/cmap-class.md), prend quatre paramètres: *KEY*, *ARG_KEY*, *VALUE*, et *ARG_VALUE*. À l'instar des classes de tableau et de liste, les classes de table peuvent stocker n'importe quel type de données. Contrairement aux tableaux et listes, qui indexent et classent les données qu'ils contiennent, les tables associent des clés et des valeurs. Vous accédez à une valeur stockée dans une table en spécifiant la clé qui lui est associée. Le paramètre *KEY* spécifie le type de données des clés utilisées pour accéder aux données stockées dans la carte. Si le type de *KEY* est une structure ou une classe, le *paramètre ARG_KEY* est généralement une référence au type spécifié dans *KEY*. Le paramètre *VALUE* spécifie le type d’éléments stockés dans la carte. Si le type de *ARG_VALUE* est une structure ou une classe, le *paramètre ARG_VALUE* est généralement une référence au type spécifié dans *VALUE*. Par exemple :

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

Le premier `MY_STRUCT` exemple stocke les valeurs, y accède `MY_STRUCT` par des clés **int** et renvoie les articles consultés par référence. Le deuxième exemple stocke des valeurs `CPerson`, y accède par des clés `CString` et retourne les références aux éléments accédés. Cet exemple peut représenter un carnet d'adresses simple où vous recherchez des personnes par leur nom de famille.

Parce que le paramètre *KEY* est de type `CString` et le paramètre *KEY_TYPE* est de type `LPCSTR`, les touches sont stockées dans la carte comme des éléments de type, `CString` mais sont référencées dans des fonctions telles que `SetAt` par des pointeurs de type `LPCSTR`. Par exemple :

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>Utilisation de modèles de collection dactylographiés

Pour utiliser les modèles de collection de pointeurs typés, vous devez connaître le type de données pouvant être stockées dans ces collections et les paramètres à utiliser dans les déclarations de collection.

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>Array typé-pointeur et utilisation de liste

Le tableau typé et les classes de liste, [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md) et [CTypedPtrList](../mfc/reference/ctypedptrlist-class.md), prendre deux paramètres: *BASE_CLASS* et *TYPE*. Ces classes peuvent stocker n’importe quel type de données, que vous spécifiez dans le paramètre *TYPE.* Ils sont dérivés de l’une des classes de collecte nontemplate qui stocke des pointeurs; vous spécifiez cette classe de base en *BASE_CLASS*. Pour les tableaux, utilisez `CObArray` ou `CPtrArray`. Pour les listes, utilisez `CObList` ou `CPtrList`.

En effet, lorsque vous déclarez une collection basée sur `CObList`, non seulement la nouvelle classe hérite des membres de sa classe de base, mais elle déclare également plusieurs opérateurs et fonctions membres de type sécurisé qui aident à assurer la cohérence des types en encapsulant des appels aux membres de la classe de base. Ces encapsulations gèrent toutes les conversions de type nécessaires. Par exemple :

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

Le premier exemple déclare un tableau de pointeurs typés, `myArray`, dérivé de `CObArray`. Le tableau stocke et retourne des pointeurs vers des objets `CPerson` (où `CPerson` est une classe dérivée de `CObject`). Vous pouvez `CObArray` appeler n’importe quelle fonction membre, `GetAt` `ElementAt` ou vous pouvez appeler le nouveau type-sûr et les fonctions ou utiliser le type-sûr **[ ]** opérateur.

Le deuxième exemple déclare une liste de pointeurs typés, `myList`, dérivée de `CPtrList`. La liste stocke et retourne des pointeurs vers des objets `MY_STRUCT`. Une classe basée sur `CPtrList` est utilisée pour stocker des pointeurs vers des objets non dérivés de `CObject`. `CTypedPtrList` a plusieurs fonctions membres de type sécurisé : `GetHead`, `GetTail`, `RemoveHead`, `RemoveTail`, `GetNext`, `GetPrev` et `GetAt`.

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>Utilisation de carte dactylographique-pointeur

La classe de carte à point type, [CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md), prend trois paramètres: *BASE_CLASS*, *KEY*, et *VALUE*. Le *BASE_CLASS* BASE_CLASS paramètre spécifie la classe à `CMapPtrToWord`partir `CMapPtrToPtr` `CMapStringToPtr`de `CMapWordToPtr` `CMapStringToOb`laquelle dériver la nouvelle classe: , , , , et ainsi de suite. *KEY* est analogue *KEY* à `CMap`KEY dans : Il spécifie le type de clé utilisée pour les plans de recherche. *VALUE* est analogue *VALUE* à `CMap`VALUE dans : Il spécifie le type d’objet stocké dans la carte. Par exemple :

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

Le premier exemple est `CMapPtrToPtr` une carte `CString` basée sur - `MY_STRUCT`il utilise des clés cartographiées pour pointers à . Vous pouvez rechercher un pointeur stocké en appelant une fonction membre de type sécurisé `Lookup`. Vous pouvez utiliser **l’opérateur [ ]** pour rechercher un pointeur stocké et l’ajouter s’il n’est pas trouvé. Vous pouvez également itérer la table à l'aide de la fonction de type sécurisé `GetNextAssoc`. Vous pouvez également appeler d'autres fonctions membres de la classe `CMapPtrToPtr`.

Le deuxième exemple est `CMapStringToOb` une carte basée sur - il `CMyObject` utilise des touches de chaîne cartographiés pour stocker des pointeurs aux objets. Vous pouvez utiliser les mêmes membres de type sécurisé décrits dans le paragraphe précédent, ou vous pouvez appeler des membres de la classe `CMapStringToOb`.

> [!NOTE]
> Si vous spécifiez un type **de classe** ou **de struct** pour le paramètre *VALUE,* plutôt qu’un pointeur ou une référence au type, la classe ou la structure doit avoir un constructeur de copie.

Pour plus d’informations, voir [Comment faire une collection type-safe](../mfc/how-to-make-a-type-safe-collection.md).

## <a name="see-also"></a>Voir aussi

[Collections](../mfc/collections.md)
