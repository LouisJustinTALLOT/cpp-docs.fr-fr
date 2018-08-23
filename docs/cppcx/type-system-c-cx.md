---
title: Système de type (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6137203176722316b802a1da5bb2e67dba36848a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594019"
---
# <a name="type-system-ccx"></a>Système de type (C++/CX)
À l’aide de l’architecture de Windows Runtime, vous pouvez utiliser C++ / c++ / CX, Visual Basic, Visual c# et JavaScript pour écrire des applications et composants qui directement accéder à l’API Windows et interagissent avec d’autres applications Windows Runtime et les composants. Les applications de plateforme de Windows universelle qui sont écrits en C++ compilent en code natif qui s’exécute directement dans l’UC. Les applications de plateforme de Windows universelle qui sont écrits en c# ou Visual Basic compilent en langage intermédiaire Microsoft (MSIL) et exécutent dans le common language runtime (CLR). Exécutent des applications universelles Windows Platform qui sont écrits en JavaScript dans un environnement d’exécution. Les composants de système d’exploitation Windows Runtime proprement dits sont écrites en C++ et exécutés en code natif. Tous ces composants et les applications de plateforme Windows universelle communiquent directement par le biais de l’interface binaire d’application Windows Runtime (ABI).  
  
 Pour activer la prise en charge pour le Windows Runtime dans un idiome C++ moderne, Microsoft a créé le C + c++ / CX. C++ / c++ / CX fournit des types de base intégrés et les implémentations de types Windows Runtime fondamentaux qui permettent aux applications C++ et les composants de communiquer à travers l’ABI avec les applications qui sont écrites dans d’autres langages. Vous pouvez utiliser n’importe quel type Windows Runtime, ou créer des classes, structs, interfaces et autres types définis par l’utilisateur qui peuvent être consommées par d’autres applications de plateforme Windows universelle et les composants. une application de plateforme Windows universelle qui est écrit en C / c++ / CX pouvez également utiliser les classes C++ habituelles et structures tant qu’ils n’ont pas une accessibilité publique.  
  
 Pour une discussion détaillée de la projection du langage C++/CX et de son fonctionnement réel, voir les billets de blog suivants :  
  
1.  [C++ / c++ / CX partie 0 sur \[n\]: Introduction](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)  
  
2.  [C++ / c++ / CX partie 1 sur \[n\]: une classe Simple](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)  
  
3.  [C++ / c++ / CX partie 2 sur \[n\]: Types avec chapeaux](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)  
  
4.  [C++ / c++ / CX partie 3 sur \[n\]: sous Construction](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)  
  
5.  [C++ / c++ / CX partie 4 sur \[n\]: les fonctions membres statiques](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)  
  
## <a name="windows-metadata-winmd-files"></a>Fichiers de métadonnées Windows (.winmd)  
 Lorsque vous compilez une application de plateforme Windows universelle qui est écrit en C++, le compilateur génère le fichier exécutable en code machine natif et qu’il génère également un fichier de métadonnées (.winmd) Windows distinct qui contient des descriptions des types Windows Runtime publics, qui incluent des classes, structures, énumérations, interfaces, interfaces paramétrables et délégués. Le format des métadonnées est semblable au format utilisé dans les assemblys .NET Framework.  Dans un composant C++, le fichier .winmd contient uniquement des métadonnées. Le code exécutable se trouve dans un fichier distinct. C’est le cas pour les composants Windows Runtime qui sont inclus avec Windows. Le nom du fichier WinMD doit correspondre à l'espace de noms racine ou en être le préfixe dans le code source. (Pour les langages .NET Framework, le fichier .winmd contient le code et les métadonnées, tout comme un assembly. NET Framework.)  
  
 Les métadonnées du fichier .winmd représentent la surface publiée de votre code. Types publiés sont visibles à d’autres plateformes Windows universelle quel que soit le langage que ces autres applications sont écrites. Par conséquent, les métadonnées ou votre code publié ne peut contenir les types spécifiés par le système de type Windows Runtime. Les constructions de langage propres à C++, telles que les classes, tableaux, modèles ou conteneurs STL normaux, ne peuvent pas être publiées dans les métadonnées, car une application cliente Javascript ou C# ne saura pas quoi faire avec.  
  
 La visibilité d'un type ou d'une méthode dans les métadonnées dépend des modificateurs d'accessibilité qui lui sont appliqués. Pour être visible, un type doit être déclaré dans un espace de noms et comme public. Une ref class non publique est autorisée comme type d'assistance interne dans votre code mais elle n'est pas visible dans les métadonnées. Même dans une classe ref, les membres ne sont pas tous nécessairement visibles. Le tableau suivant répertorie la relation entre les spécificateurs d’accès C++ dans une classe ref publique et la visibilité des métadonnées Windows Runtime :  
  
|||  
|-|-|  
|**Publié dans les métadonnées**|**Non publié dans les métadonnées**|  
|public|private|  
|protected|internal|  
|protégé public|protégé privé|  
  
 Vous pouvez utiliser l' **Explorateur d'objets** pour afficher le contenu des fichiers .winmd. Les composants Windows Runtime qui sont inclus avec Windows sont dans le fichier Windows.winmd. Le fichier default.winmd contient les types fondamentaux qui sont utilisées en C / c++ / CX et platform.winmd contient les types supplémentaires à partir de l’espace de noms de plateforme. Par défaut, ces trois fichiers .winmd sont inclus dans chaque projet C++ pour les applications de plateforme Windows universelle.  
  
> [!TIP]
>  Les types présents dans [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) n'apparaissent pas dans le fichier .winmd car ils ne sont pas publics. Ce sont des implémentations propres à C++ privées des interfaces définies dans `Windows::Foundation::Collections`. Une application Windows Runtime qui est écrit en JavaScript ou c# ne sait pas qu’un [classe Platform::Collections :: Vector](../cppcx/platform-collections-vector-class.md) est, mais elle peut consommer un `Windows::Foundation::Collections::IVector`. Les types `Platform::Collections` sont définis dans collection.h.  
  
## <a name="windows-runtime-type-system-in-ccx"></a>Système de type Windows Runtime en C / c++ / CX  
 Les sections suivantes décrivent les principales fonctionnalités du système de type Windows Runtime et comment elles sont prises en charge en C / c++ / CX.  
  
### <a name="namespaces"></a>Espaces de noms  
 Tous les types Windows Runtime doivent être déclarés dans un espace de noms ; l’API Windows elle-même est organisée par espaces de noms. Un fichier .winmd doit avoir le même nom que l'espace de noms racine. Par exemple, une classe nommée A.B.C.MyClass peut être instanciée uniquement si elle est définie dans un fichier de métadonnées nommé A.winmd, A.B.winmd ou A.B.C.winmd. Il n'est pas requis que le nom de la DLL corresponde au nom du fichier .winmd.  
  
 L'API Windows elle-même a été réinventée sous la forme d'une bibliothèque de classes correctement factorisées, organisée par espaces de noms.  Tous les composants Windows Runtime sont déclarés dans les espaces de noms Windows.*.  
  
 Pour plus d’informations, consultez [espaces de noms et la visibilité du Type](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### <a name="fundamental-types"></a>Types fondamentaux  
 Le Runtime Windows définit les types fondamentaux suivants, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, valeur booléenne et chaîne. C++ / c++ / CX prend en charge les types numériques fondamentaux dans son espace de noms par défaut en tant qu’uint16, uint32, uint64, int16, int32, int64, float32, float64 et char16. Les types Boolean et String sont également définis dans l'espace de noms Platform.  
  
 C++ / c++ / CX définit également uint8, équivalent à `unsigned char`, qui n’est pas pris en charge dans le Runtime Windows et ne peut pas être utilisé dans les API publiques.  
  
 Il est possible de rendre Nullable un type fondamental en l'encapsulant dans une [interface Platform::IBox](../cppcx/platform-ibox-interface.md) . Pour plus d'informations, consultez [Classes de valeur et structures de valeur](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Pour plus d'informations sur les types fondamentaux, consultez [Types fondamentaux](../cppcx/fundamental-types-c-cx.md)  
  
### <a name="strings"></a>Chaînes  
 Une chaîne de Windows Runtime est une séquence immuable de caractères UNICODE 16 bits. Une chaîne de Windows Runtime est projetée comme `Platform::String^`. Cette classe fournit des méthodes pour la construction, la manipulation, et la conversion des chaînes vers et à partir de `wchar_t`.  
  
 Pour plus d'informations, consultez [Chaînes](../cppcx/strings-c-cx.md).  
  
### <a name="arrays"></a>Tableaux  
 Le Runtime Windows prend en charge les tableaux 1D de n’importe quel type. Les tableaux de tableaux ne sont pas pris en charge.  En C / c++ / CX, les tableaux Windows Runtime sont projetés en tant que le [Platform::Array, classe](../cppcx/platform-array-class.md).  
  
 Pour plus d’informations, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)  
  
### <a name="ref-classes-and-structs"></a>Classes et structures de référence  
 Une classe Windows Runtime est projetée en C / c++ / CX en tant que classe ref ou un struct ref, car elles sont copiées par référence. La gestion de mémoire pour les classes ou structures ref est traitée de façon transparente au moyen d'un décompte de références. Lorsque la dernière référence à un objet devient hors de portée, l'objet est détruit. Une classe ou structure ref peut :  
  
-   Contenir comme membres des constructeurs, méthodes, propriétés et événements. Ces membres peuvent avoir un accès public, privé, protégé ou interne.  
  
-   Contenir des définitions d'énumération, de structure ou de classe imbriquées privées.  
  
-   Hériter directement d'une classe de base et implémenter un nombre quelconque d'interfaces. Toutes les classes ref sont implicitement convertibles en [Platform::Object Class](../cppcx/platform-object-class.md) et peuvent substituer ses méthodes virtuelles, par exemple [Object::ToString](../cppcx/platform-object-class.md#tostring).  
  
 Une classe de référence qui a un constructeur public doit être déclarée comme sealed, pour empêcher une dérivation supplémentaire.  
  
 Pour plus d'informations, consultez [Classes et structures de référence](../cppcx/ref-classes-and-structs-c-cx.md)  
  
### <a name="value-classes-and-structs"></a>Classes de valeur et structures de valeur  
 Une classe de valeur ou une structure de valeur représente une structure de données de base et contient uniquement des champs, qui peuvent être des classes de valeur, des structures de valeur ou de type `Platform::String^`.  Les structures de valeur et les classes de valeur sont copiées par valeur.  
  
 Il est possible de rendre Nullable un struct value en l'encapsulant dans une interface IBox.  
  
 Pour plus d'informations, consultez [Classes de valeur et structures de valeur](../cppcx/value-classes-and-structs-c-cx.md).  
  
### <a name="partial-classes"></a>Classes partielles  
 La fonctionnalité de classe partielle permet à une classe d'être définie sur plusieurs fichiers. Elle sert avant tout à permettre aux outils de génération de code tels que l'éditeur XAML de modifier un fichier sans toucher au fichier que vous modifiez.  
  
 Pour plus d'informations, consultez [Classes partielles](../cppcx/partial-classes-c-cx.md)  
  
### <a name="properties"></a>Properties  
 Une propriété est un membre de données public de n’importe quel type de Runtime de Windows et est implémentée comme une paire de méthodes get/set. Le code client accède à une propriété comme s'il s'agissait d'un champ public. Une propriété qui ne requiert aucun code get ou set personnalisé est appelée *propriété triviale* et peut être déclarée sans méthodes get ou set explicites.  
  
 Pour plus d'informations, consultez [Propriétés](../cppcx/properties-c-cx.md).  
  
### <a name="windows-runtime-collections-in-ccx"></a>Collections Windows Runtime en C / c++ / CX  
 Le Runtime Windows définit un ensemble d’interfaces pour les types de collection que chaque langage implémente à sa manière. C++ / c++ / CX fournit des implémentations dans les [classe Platform::Collections :: Vector](../cppcx/platform-collections-vector-class.md), [classe Platform::Collections :: Map](../cppcx/platform-collections-map-class.md)et d’autres types de collection concrets associés, qui sont compatibles avec leurs Équivalents STL (Template Library) standard.  
  
 Pour plus d’informations, consultez [Collections](../cppcx/collections-c-cx.md).  
  
### <a name="template-ref-classes"></a>Classes ref de modèle  
 Les classes ref privées et internes peuvent être basées sur un modèle et spécialisées.  
  
 Pour plus d'informations, consultez [Classes ref de modèle](../cppcx/template-ref-classes-c-cx.md).  
  
### <a name="interfaces"></a>Interfaces  
 Une interface Windows Runtime définit un ensemble de propriétés publiques, méthodes et événements qu’une classe ref ou une structure ref doit implémenter si elle hérite de l’interface.  
  
 Pour plus d’informations, consultez [Interfaces](../cppcx/interfaces-c-cx.md).  
  
### <a name="enums"></a>Enums  
 Une classe enum dans Windows Runtime ressemble à un enum limité en C++. Le type sous-jacent est int32 sauf si l'attribut [Flags] est appliqué, auquel cas le type sous-jacent est uint32.  
  
 Pour plus d'informations, consultez [Énumérations](../cppcx/enums-c-cx.md).  
  
### <a name="delegates"></a>Délégués  
 Un délégué dans le Windows Runtime est analogue à un objet std::function en C++. C'est un type spécial de classe de référence qui est utilisée pour appeler les fonctions fournies par le client qui ont des signatures compatibles.  Les délégués sont couramment utilisés dans le Runtime Windows comme type d’un événement.  
  
 Pour plus d’informations, consultez [Délégués](../cppcx/delegates-c-cx.md).  
  
### <a name="exceptions"></a>Exceptions  
 Dans C++/CX, vous pouvez intercepter les types d'exceptions personnalisés, les types [std::exception](../standard-library/exception-class.md) et les types [Platform::Exception](../cppcx/platform-exception-class.md) .  
  
 Pour plus d'informations, consultez [Exceptions](../cppcx/exceptions-c-cx.md).  
  
### <a name="events"></a>Événements  
 Un événement est un membre public d'une classe ou structure ref dont le type est un type de délégué. Un événement ne peut être appelé, c'est-à-dire déclenché, que par la classe propriétaire. Toutefois, le code client peut fournir ses propres fonctions, connues sous le nom de gestionnaires d'événements. Elles sont appelées lorsque la classe propriétaire déclenche l'événement.  
  
 Pour plus d'informations, consultez [Événements](../cppcx/events-c-cx.md).  
  
### <a name="casting"></a>Cast  
 C++/CX prend en charge les opérateurs de cast C++ standard [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)et [reinterpret_cast](../cpp/reinterpret-cast-operator.md), ainsi que l'opérateur **safe_cast** propre à C++/CX.  
  
 Pour plus d'informations, consultez [Cast](../cppcx/casting-c-cx.md).  
  
### <a name="boxing"></a>Boxing  
 Une variable convertie (boxed) est un type valeur encapsulé dans un type référence dans les situations où la sémantique de référence est requise.  
  
 Pour plus d'informations, consultez [Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="attributes"></a>Attributs  
 Un attribut est une valeur de métadonnées qui peut être appliquée à n’importe quel type de Runtime de Windows ou un membre de type et peut être inspectée au moment de l’exécution. Le Runtime Windows définit un ensemble d’attributs communs dans le `Windows::Foundation::Metadata` espace de noms. Attributs définis par l’utilisateur sur les interfaces publiques ne sont pas pris en charge par Windows Runtime dans cette version.  
  
## <a name="api-deprecation"></a>API déconseillées  
 Décrit comment marquer les API publiques comme étant déconseillées, à l’aide de l’attribut même est utilisé par les types de système de Windows Runtime.  
  
 Pour plus d’informations, consultez [dépréciation des types et membres](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
