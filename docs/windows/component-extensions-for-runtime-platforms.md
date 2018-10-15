---
title: Extensions de composant pour .NET et UWP | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45f83fbaaa867e2f58e329d8531259fa3751a521
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328413"
---
# <a name="component-extensions-for-net-and-uwp"></a>Extensions de composant pour .NET et UWP

La norme C++ permet aux fournisseurs de compilateur fournir des extensions non standards du langage. Microsoft fournit des extensions pour vous aider à vous connecter native C++ code pour le code qui s’exécute sur le .NET Framework ou de la plateforme universelle Windows (UWP). Les extensions .NET sont appelées C + c++ / CLI et produire le code qui s’exécute dans le .NET gérés de l’environnement d’exécution qui est appelé le Common Language Runtime (CLR). Les extensions UWP sont appelées C + c++ / CX et ils produisent en code machine natif.

> [!NOTE]
> Pour les nouvelles applications, nous vous recommandons d’utiliser C++ / c++ / WinRT plutôt que C++ / c++ / CX. C++ / c++ / WinRT est une nouvelle, standard C ++ 17 projection de langage pour Windows Runtime APIs. Nous continuerons à prendre en charge de C++ / c++ / CX et WRL, mais vous recommandons vivement que les nouvelles applications utiliser C++ / c++ / WinRT. Pour plus d’informations, consultez [C++ / c++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Deux runtimes, un ensemble d’extensions

C++ / c++ / CLI étend la norme ISO/ANSI C++ et est défini sous Ecma C++ / c++ / CLI Standard. Pour plus d’informations, consultez [programmation .NET avec C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

C++ / c++ / extensions CX sont un sous-ensemble de C / c++ / CLI. Bien que la syntaxe d’extension est identique dans la plupart des cas, le code généré varie selon que vous spécifiez la `/ZW` cible UWP, l’option du compilateur ou le `/clr` option pour .NET. Ces commutateurs sont définis automatiquement quand vous utilisez Visual Studio pour créer un projet.

## <a name="data-type-keywords"></a>Mots clés de type de données

Les extensions de langage incluent *agréger les mots clés*, qui se composent de deux jetons séparés par un espace blanc. Les jetons peuvent avoir une signification précise quand ils sont utilisés séparément et une autre signification quand ils sont utilisés ensemble. Par exemple, le mot « ref » est un identificateur ordinaire et le mot « class » est un mot clé qui déclare une classe native. Mais quand ces mots sont combinés pour former **classe ref**, le mot clé d’agrégation qui en résulte déclare une entité qui est appelée un *classe runtime*.

Les extensions incluent également *contextuelle* mots clés. Un mot clé est considéré comme contextuel en fonction du type d'instruction qui le contient et de son positionnement dans cette instruction. Par exemple, le jeton « property » peut être un identificateur ou il peut déclarer un type spécial de membre de classe publique.

Le tableau suivant répertorie les mots clés de l'extension du langage C++.

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**classe ref**<br /><br /> **struct ref**|Non|Déclare une classe.|[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)|
|**classe value**<br /><br /> **struct Value**|Non|Déclare une classe de valeur.|[Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)|
|**classe d’interface**<br /><br /> **struct d’interface**|Non|Déclare une interface.|[classe d’interface](../windows/interface-class-cpp-component-extensions.md)|
|**enum, classe**<br /><br /> **enum struct**|Non|Déclare une énumération.|[enum, classe](../windows/enum-class-cpp-component-extensions.md)|
|**propriété**|Oui|Déclare une propriété.|[propriété](../windows/property-cpp-component-extensions.md)|
|**delegate**|Oui|Déclare un délégué.|[délégué (C++ / c++ / CLI et c++ / CX)](../windows/delegate-cpp-component-extensions.md)|
|**event**|Oui|Déclare un événement.|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Spécificateurs de substitution

Vous pouvez utiliser les mots clés suivants pour qualifier le comportement de substitution pour la dérivation. Bien que le **nouveau** mot clé n’est pas une extension de C++, il est répertorié ici car il peut être utilisé dans un contexte supplémentaire. Certains spécificateurs sont également valides pour la programmation native. Pour plus d’informations, consultez [Comment : déclarer des spécificateurs de substitution dans les Compilations natives (C++ / c++ / CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Oui|Indique que les fonctions ou classes sont abstraites.|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|Non|Indique qu'une fonction n'est pas une substitution d'une version de la classe de base.|[New (nouvel emplacement dans vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Oui|Indique qu'une méthode doit être une substitution d'une version de la classe de base.|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|Oui|Empêche les classes d'être utilisées comme classes de base.|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Mots clés pour les génériques

Les mots clés suivants ont été ajoutés pour prendre en charge des types génériques. Pour plus d’informations, consultez la page [Génériques](../windows/generics-cpp-component-extensions.md).

|Mot clé|Contextuel|Objectif|
|-------------|-----------------------|-------------|
|**Générique**|Non|Déclare un type générique.|
|**where**|Oui|Spécifie les contraintes appliquées à un paramètre de type générique.|

## <a name="miscellaneous-keywords"></a>Mots clés divers

Les mots clés suivants ont été ajoutés aux extensions C++.

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**finally**|Oui|Indique le comportement de gestion des exceptions par défaut.|[Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|Non|Énumère les éléments d’une collection.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Non|Alloue des types sur le tas récupéré par le garbage collector. Utilisez à la place de **nouveau** et **supprimer**.|[gcnew nouvelle, ref](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**ref nouveau**|Oui|Alloue un type Windows Runtime. Utilisez à la place de **nouveau** et **supprimer**.|[gcnew nouvelle, ref](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Oui|Indique qu’un membre peut uniquement être initialisé lors de la déclaration ou dans un constructeur statique.|[initonly (C++-CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Oui|Crée une variable littérale.|[literal](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|Non|Indique qu'un handle ou pointeur ne pointe pas vers un objet.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Constructions de modèle

Les constructions de langage suivantes sont implémentées comme modèles, plutôt que comme mots clés. Si vous spécifiez l'option de compilateur `/ZW`, elles sont définies dans l'espace de noms `lang`. Si vous spécifiez l'option de compilateur `/clr`, elles sont définies dans l'espace de noms `cli`.

|Mot clé|Objectif|Référence|
|-------------|-------------|---------------|
|**array**|Déclare un tableau.|[Tableaux](../windows/arrays-cpp-component-extensions.md)|
|**interior_ptr**|(CLR uniquement) Pointe vers des données dans un type de référence.|[interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|(CLR uniquement) Pointe vers des types de référence CLR pour supprimer temporairement le système de garbage collection.|[pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)|
|**safe_cast**|Détermine et exécute la méthode de casting optimale pour un type de runtime.|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**typeid**|(CLR uniquement) Récupère un objet <xref:System.Type?displayProperty=fullName> qui décrit le type ou l'objet donné.|[typeid](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Déclarateurs

Les déclarateurs de type suivants demandent au runtime de gérer automatiquement la durée de vie et la suppression des objets alloués.

|Opérateur|Objectif|Référence|
|--------------|-------------|---------------|
|`^`|Déclare un handle à un objet ; Autrement dit, un pointeur vers un objet Windows Runtime ou CLR qui est automatiquement supprimé quand il n’est plus utilisable.|[Handle de l’opérateur Object (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Déclare une référence de suivi ; Autrement dit, une référence à un objet Windows Runtime ou CLR qui est automatiquement supprimé quand il n’est plus utilisable.|[Opérateur de référence de suivi](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Constructions supplémentaires et rubriques connexes

Cette section répertorie les constructions de programmation supplémentaires, ainsi que les rubriques qui se rapportent au CLR.

|Rubrique|Description|
|-----------|-----------------|
|[__identifier (C++-CLI)](../windows/identifier-cpp-cli.md)|(Windows Runtime et CLR) Permet d’utiliser des mots clés comme identificateurs.|
|[Listes d’arguments de variable (...) (C++-CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime et CLR) Permet à une fonction à prendre un nombre variable d’arguments.|
|[Équivalents .NET Framework des types natifs C++ (C++-CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Répertorie les types CLR qui sont utilisés à la place des types intégraux C++.|
|[AppDomain](../cpp/appdomain.md) **__declspec** modificateur|**__declspec** modificateur qui impose que les variables statiques et globales existent par appdomain.|
|[Les Casts de Style C avec /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|Décrit comment les casts de style C sont interprétées.|
|[__clrcall](../cpp/clrcall.md) convention d’appel|Indique la convention d’appel conforme au CLR.|
|`__cplusplus_cli`|[Macros prédéfinies](../preprocessor/predefined-macros.md)|
|[Attributs personnalisés](../windows/custom-attributes-cpp.md)|Décrit comment définir vos propres attributs CLR.|
|[Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)|Fournit une vue d'ensemble de la gestion des exceptions.|
|[Substitutions explicites](../windows/explicit-overrides-cpp-component-extensions.md)|Montre comment les fonctions membres peuvent substituer les membres arbitraires.|
|[Assemblys friend (C++)](../dotnet/friend-assemblies-cpp.md)|Explique comment un assembly client peut accéder à tous les types dans un composant d'assembly.|
|[Conversion boxing](../windows/boxing-cpp-component-extensions.md)|Montre les conditions dans lesquelles les types de valeur sont boxed.|
|[Prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|Explique comment détecter les caractéristiques des types au moment de la compilation.|
|[Managed, unmanaged](../preprocessor/managed-unmanaged.md) pragmas|Montre comment les fonctions managées et non managées peuvent coexister dans le même module.|
|[processus](../cpp/process.md) **__declspec** modificateur|**__declspec** modificateur qui impose que les variables statiques et globales existent par processus.|
|[Réflexion (C++-CLI)](../dotnet/reflection-cpp-cli.md)|Montre la version CLR des informations de type au moment de l'exécution.|
|[String](../windows/string-cpp-component-extensions.md)|Décrit la conversion du compilateur des littéraux de chaîne en <xref:System.String>.|
|[Transfert de type (C++-CLI)](../windows/type-forwarding-cpp-cli.md)|Permet le déplacement d'un type dans un assembly d'expédition vers un autre assembly afin que le code client n'ait pas besoin d'être recompilé.|
|[Attributs définis par l’utilisateur](../windows/user-defined-attributes-cpp-component-extensions.md)|Montre les attributs définis par l'utilisateur.|
|[Directive #using](../preprocessor/hash-using-directive-cpp.md)|Importe des assemblys externes.|
|[Documentation XML](../ide/xml-documentation-visual-cpp.md)|Explique la documentation du code XML à l’aide de [/doc (traiter les commentaires de Documentation) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)