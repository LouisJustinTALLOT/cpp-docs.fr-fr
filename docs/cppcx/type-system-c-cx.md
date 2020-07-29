---
title: Système de type (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: b9d26f0fc79b2dc5000be6e6a06f51efd3f0b53f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221547"
---
# <a name="type-system-ccx"></a>Système de type (C++/CX)

À l’aide de l’architecture Windows Runtime, vous pouvez utiliser C++/CX, Visual Basic, Visual C# et JavaScript pour écrire des applications et des composants qui accèdent directement à l’API Windows et interagissent avec d’autres applications et composants Windows Runtime. Plateforme Windows universelle applications écrites en C++ se compilent en code natif qui s’exécute directement dans le processeur. Plateforme Windows universelle les applications écrites en C# ou Visual Basic compilées en langage MSIL (Microsoft Intermediate Language) et s’exécutent dans le common language runtime (CLR). Plateforme Windows universelle les applications écrites en JavaScript s’exécutent dans un environnement d’exécution. Les composants du système d’exploitation Windows Runtime eux-mêmes sont écrits en C++ et s’exécutent en tant que code natif. Tous ces composants et applications plateforme Windows universelle communiquent directement par le biais de l’interface de binaire d’application (ABI) Windows Runtime.

Pour activer la prise en charge de l’Windows Runtime dans un idiome moderne C++, Microsoft a créé le C++/CX. C++/CX fournit des types de base intégrés et des implémentations de types de Windows Runtime fondamentaux qui permettent aux applications et composants C++ de communiquer à travers l’ABI avec les applications écrites dans d’autres langages. Vous pouvez utiliser n’importe quel type de Windows Runtime ou créer des classes, des structures, des interfaces et d’autres types définis par l’utilisateur qui peuvent être utilisés par d’autres applications et composants plateforme Windows universelle. une plateforme Windows universelle application écrite en C++/CX peut également utiliser des classes et des structures C++ normales, à condition qu’elles n’aient pas d’accessibilité publique.

Pour une discussion détaillée de la projection du langage C++/CX et de son fonctionnement réel, voir les billets de blog suivants :

- [C++/CX partie 0 sur \[ n \] : présentation](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)

- [C++/CX partie 1 de \[ n \] : classe simple](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)

- [C++/CX partie 2 sur \[ n \] : types qui ont des chapeaux](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)

- [C++/CX partie 3 sur \[ n \] : en cours de construction](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)

- [C++/CX, partie 4 sur \[ n \] : fonctions membres statiques](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)

## <a name="windows-metadata-winmd-files"></a>Fichiers de métadonnées Windows (.winmd)

Quand vous compilez une plateforme Windows universelle application écrite en C++, le compilateur génère l’exécutable dans le code machine natif et génère également un fichier de métadonnées Windows (. winmd) distinct qui contient les descriptions des types de Windows Runtime publics, qui incluent des classes, des structures, des énumérations, des interfaces, des interfaces paramétrables et des délégués. Le format des métadonnées est semblable au format utilisé dans les assemblys .NET Framework.  Dans un composant C++, le fichier .winmd contient uniquement des métadonnées. Le code exécutable se trouve dans un fichier distinct. C’est le cas pour les composants Windows Runtime inclus avec Windows. Le nom du fichier WinMD doit correspondre à l'espace de noms racine ou en être le préfixe dans le code source. (Pour les langages .NET Framework, le fichier .winmd contient le code et les métadonnées, tout comme un assembly. NET Framework.)

Les métadonnées du fichier .winmd représentent la surface publiée de votre code. Les types publiés sont visibles par d’autres plateformes Windows universelles quel que soit le langage dans lequel ces autres applications sont écrites. Par conséquent, les métadonnées ou votre code publié ne peuvent contenir que des types spécifiés par le système de type Windows Runtime. Les constructions de langage propres à C++, telles que les classes, tableaux, modèles ou conteneurs STL normaux, ne peuvent pas être publiées dans les métadonnées, car une application cliente Javascript ou C# ne saura pas quoi faire avec.

La visibilité d'un type ou d'une méthode dans les métadonnées dépend des modificateurs d'accessibilité qui lui sont appliqués. Pour être visible, un type doit être déclaré dans un espace de noms et comme public. Une ref class non publique est autorisée comme type d'assistance interne dans votre code mais elle n'est pas visible dans les métadonnées. Même dans une classe ref, les membres ne sont pas tous nécessairement visibles. Le tableau suivant répertorie la relation entre les spécificateurs d’accès C++ dans une classe ref publique et Windows Runtime la visibilité des métadonnées :

|||
|-|-|
|**Publié dans les métadonnées**|**Non publié dans les métadonnées**|
|public|private|
|protected|interne|
|protégé public|protégé privé|

Vous pouvez utiliser l' **Explorateur d'objets** pour afficher le contenu des fichiers .winmd. Les composants Windows Runtime inclus avec Windows se trouvent dans le fichier Windows. winmd. Le fichier default. winmd contient les types fondamentaux utilisés dans C++/CX, et Platform. winmd contient des types supplémentaires de l’espace de noms Platform. Par défaut, ces trois fichiers. winmd sont inclus dans chaque projet C++ pour les applications plateforme Windows universelle.

> [!TIP]
> Les types présents dans [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) n'apparaissent pas dans le fichier .winmd car ils ne sont pas publics. Ce sont des implémentations propres à C++ privées des interfaces définies dans `Windows::Foundation::Collections`. Une Windows Runtime application écrite en JavaScript ou C# ne sait pas ce qu’est une [classe Platform :: Collections :: Vector](../cppcx/platform-collections-vector-class.md) , mais elle peut consommer un `Windows::Foundation::Collections::IVector` . Les types `Platform::Collections` sont définis dans collection.h.

## <a name="windows-runtime-type-system-in-ccx"></a>Système de type Windows Runtime en C++/CX

Les sections suivantes décrivent les principales fonctionnalités du système de type Windows Runtime et comment elles sont prises en charge en C++/CX.

### <a name="namespaces"></a>Espaces de noms

Tous les types de Windows Runtime doivent être déclarés dans un espace de noms ; l’API Windows elle-même est organisée par espaces de noms. Un fichier .winmd doit avoir le même nom que l'espace de noms racine. Par exemple, une classe nommée A.B.C.MyClass peut être instanciée uniquement si elle est définie dans un fichier de métadonnées nommé A.winmd, A.B.winmd ou A.B.C.winmd. Il n'est pas requis que le nom de la DLL corresponde au nom du fichier .winmd.

L'API Windows elle-même a été réinventée sous la forme d'une bibliothèque de classes correctement factorisées, organisée par espaces de noms.  Tous les composants Windows Runtime sont déclarés dans les espaces de noms Windows. *.

Pour plus d’informations, consultez [espaces de noms et visibilité de type](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Types fondamentaux

L’Windows Runtime définit les types fondamentaux suivants : UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, double, Char16, Boolean et String. C++/CX prend en charge les types numériques fondamentaux dans son espace de noms par défaut sous la forme UInt16, UInt32, UInt64, Int16, Int32, Int64, float32, float64 et char16. Les types Boolean et String sont également définis dans l'espace de noms Platform.

C++/CX définit le UInt8, **`unsigned char`** qui est équivalent à, qui n’est pas pris en charge dans le Windows Runtime et ne peut pas être utilisé dans les API publiques.

Il est possible de rendre Nullable un type fondamental en l'encapsulant dans une [interface Platform::IBox](../cppcx/platform-ibox-interface.md) . Pour plus d'informations, consultez [Classes de valeur et structures de valeur](../cppcx/value-classes-and-structs-c-cx.md).

Pour plus d'informations sur les types fondamentaux, consultez [Types fondamentaux](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Chaînes

Une chaîne Windows Runtime est une séquence immuable de caractères UNICODE 16 bits. Une chaîne de Windows Runtime est projetée comme `Platform::String^` . Cette classe fournit des méthodes pour la construction, la manipulation et la conversion de chaînes vers et à partir de **`wchar_t`** .

Pour plus d'informations, consultez [Chaînes](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Tableaux

Le Windows Runtime prend en charge les tableaux unidimensionnels de tout type. Les tableaux de tableaux ne sont pas pris en charge.  En C++/CX, les tableaux Windows Runtime sont projetés en tant que [classe Platform :: Array](../cppcx/platform-array-class.md).

Pour plus d’informations, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Classes et structures de référence

Une classe Windows Runtime est projetée en C++/CX comme une classe ref ou un struct REF, car ils sont copiés par référence. La gestion de mémoire pour les classes ou structures ref est traitée de façon transparente au moyen d'un décompte de références. Lorsque la dernière référence à un objet devient hors de portée, l'objet est détruit. Une classe ou structure ref peut :

- Contenir comme membres des constructeurs, méthodes, propriétés et événements. Ces membres peuvent avoir un accès public, privé, protégé ou interne.

- Contenir des définitions d'énumération, de structure ou de classe imbriquées privées.

- Hériter directement d'une classe de base et implémenter un nombre quelconque d'interfaces. Toutes les classes ref sont implicitement convertibles en [Platform::Object Class](../cppcx/platform-object-class.md) et peuvent substituer ses méthodes virtuelles, par exemple [Object::ToString](../cppcx/platform-object-class.md#tostring).

Une classe de référence qui a un constructeur public doit être déclarée comme sealed, pour empêcher une dérivation supplémentaire.

Pour plus d’informations, consultez [classes REF et structs](../cppcx/ref-classes-and-structs-c-cx.md) .

### <a name="value-classes-and-structs"></a>Classes de valeur et structures de valeur

Une classe de valeur ou une structure de valeur représente une structure de données de base et contient uniquement des champs, qui peuvent être des classes de valeur, des structures de valeur ou de type `Platform::String^`.  Les structures de valeur et les classes de valeur sont copiées par valeur.

Il est possible de rendre Nullable un struct value en l'encapsulant dans une interface IBox.

Pour plus d'informations, consultez [Classes de valeur et structures de valeur](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Classes partielles

La fonctionnalité de classe partielle permet à une classe d'être définie sur plusieurs fichiers. Elle sert avant tout à permettre aux outils de génération de code tels que l'éditeur XAML de modifier un fichier sans toucher au fichier que vous modifiez.

Pour plus d'informations, consultez [Classes partielles](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Propriétés

Une propriété est un membre de données public de n’importe quel type de Windows Runtime et est implémentée en tant que paire de méthodes obtenir/définir. Le code client accède à une propriété comme s'il s'agissait d'un champ public. Une propriété qui ne requiert aucun code get ou set personnalisé est appelée *propriété triviale* et peut être déclarée sans méthodes get ou set explicites.

Pour plus d'informations, consultez [Propriétés](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Collections Windows Runtime en C++/CX

Le Windows Runtime définit un jeu d’interfaces pour les types de collection que chaque langage implémente de manière autonome. C++/CX fournit des implémentations dans la classe [Platform :: Collections :: Vector](../cppcx/platform-collections-vector-class.md), [plate-forme :: Collections :: Map](../cppcx/platform-collections-map-class.md)et d’autres types de collections concrets connexes, qui sont compatibles avec leurs équivalents STL (Standard Template Library).

Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Classes ref de modèle

Les classes ref privées et internes peuvent être basées sur un modèle et spécialisées.

Pour plus d'informations, consultez [Classes ref de modèle](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Interfaces

Une interface Windows Runtime définit un ensemble de propriétés, méthodes et événements publics qu’une classe ref ou un struct ref doit implémenter si elle hérite de l’interface.

Pour plus d'informations, consultez [Interfaces](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Énumérations

Une classe enum dans Windows Runtime ressemble à une énumération délimitée en C++. Le type sous-jacent est int32 sauf si l'attribut [Flags] est appliqué, auquel cas le type sous-jacent est uint32.

Pour plus d'informations, consultez [Énumérations](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Délégués

Un délégué dans le Windows Runtime est analogue à un objet std :: function en C++. C'est un type spécial de classe de référence qui est utilisée pour appeler les fonctions fournies par le client qui ont des signatures compatibles.  Les délégués sont le plus souvent utilisés dans le Windows Runtime en tant que type d’événement.

Pour plus d'informations, consultez [Délégués](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Exceptions

Dans C++/CX, vous pouvez intercepter les types d'exceptions personnalisés, les types [std::exception](../standard-library/exception-class.md) et les types [Platform::Exception](../cppcx/platform-exception-class.md) .

Pour plus d'informations, consultez [Exceptions](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Événements

Un événement est un membre public d'une classe ou structure ref dont le type est un type de délégué. Un événement ne peut être appelé, c'est-à-dire déclenché, que par la classe propriétaire. Toutefois, le code client peut fournir ses propres fonctions, connues sous le nom de gestionnaires d'événements. Elles sont appelées lorsque la classe propriétaire déclenche l'événement.

Pour plus d’informations, consultez [Événements](../cppcx/events-c-cx.md).

### <a name="casting"></a>Cast

C++/CX prend en charge les opérateurs de cast C++ standard [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)et [reinterpret_cast](../cpp/reinterpret-cast-operator.md), ainsi que l'opérateur **safe_cast** propre à C++/CX.

Pour plus d'informations, consultez [Cast](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Boxing

Une variable convertie (boxed) est un type valeur encapsulé dans un type référence dans les situations où la sémantique de référence est requise.

Pour plus d'informations, consultez [Boxing](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Attributs

Un attribut est une valeur de métadonnées qui peut être appliquée à tout type de Windows Runtime ou membre de type et peut être inspectée au moment de l’exécution. L’Windows Runtime définit un ensemble d’attributs communs dans l' `Windows::Foundation::Metadata` espace de noms. Les attributs définis par l’utilisateur sur les interfaces publiques ne sont pas pris en charge par les Windows Runtime dans cette version.

## <a name="api-deprecation"></a>API déconseillées

Décrit comment marquer les API publiques comme dépréciées à l’aide du même attribut que celui utilisé par les types de système Windows Runtime.

Pour plus d’informations, consultez [dépréciation des types et des membres](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
