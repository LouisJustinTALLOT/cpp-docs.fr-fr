---
title: Extensions de composants pour .NET et UWP
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 1e47a138fece021cf015884222d8cf5c766655fd
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274679"
---
# <a name="component-extensions-for-net-and-uwp"></a>Extensions de composants pour .NET et UWP

Le langage C++ standard permet aux fournisseurs de compilateur de fournir des extensions non standard au langage. Microsoft fournit des extensions pour vous aider à connecter du code C++ natif à du code qui fonctionne sur .NET Framework ou la plateforme Windows universelle (UWP). Les extensions .NET sont appelées C++/CLI et produisent du code qui fonctionne dans l’environnement d’exécution managé .NET appelé le common language runtime (CLR). Les extensions UWP sont appelées C++/CX et produisent du code machine natif.

> [!NOTE]
> Pour les nouvelles applications, nous recommandons l’utilisation de C++/WinRT plutôt que C++/CX. C++/ WinRT est une nouvelle projection du langage C++17 standard pour les API Windows Runtime. Nous continuerons de prendre en charge les langages C++/CX et WRL, mais recommandons vivement l’utilisation du langage C++/WinRT avec des nouvelles applications. Pour plus d’informations, consultez [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Deux runtimes, un ensemble d’extensions

C++/CLI étend la norme ISO/ANSI C++. Sa définition entre dans la norme Ecma C++/CLI. Pour plus d’informations, consultez [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Les extensions C++/CX représentent un sous-ensemble de C++/CLI. Bien que la syntaxe d’extension soit identique dans la plupart des cas, le code généré sera différent selon si vous spécifiez l’option de compilateur `/ZW` pour cibler UWP, ou l’option `/clr` pour cibler .NET. Ces commutateurs sont définis automatiquement quand vous utilisez Visual Studio pour créer un projet.

## <a name="data-type-keywords"></a>Mots clés de type de données

Les extensions de langage incluent des *mots clés d’agrégation*, constitués de deux jetons séparés par un espace blanc. Les jetons peuvent avoir une signification précise quand ils sont utilisés séparément et une autre signification quand ils sont utilisés ensemble. Par exemple, le mot « ref » est un identificateur ordinaire et le mot « class » est un mot clé qui déclare une classe native. Mais quand ces mots sont combinés pour former **ref class**, le mot clé d’agrégation obtenu permet de déclarer une entité connue en tant que *classe runtime*.

Les extensions incluent également des mots clés *contextuels*. Un mot clé est considéré comme contextuel en fonction du type d'instruction qui le contient et de son positionnement dans cette instruction. Par exemple, le jeton « property » peut être un identificateur ou il peut déclarer un type spécial de membre de classe publique.

Le tableau suivant répertorie les mots clés de l'extension du langage C++.

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|Non|Déclare une classe.|[Classes et structs](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|Non|Déclare une classe de valeur.|[Classes et structs](classes-and-structs-cpp-component-extensions.md)|
|**interface, classe**<br /><br /> **interface struct**|Non|Déclare une interface.|[interface, classe](interface-class-cpp-component-extensions.md)|
|**enum, classe**<br /><br /> **enum struct**|Non|Déclare une énumération.|[enum, classe](enum-class-cpp-component-extensions.md)|
|**propriété**|Oui|Déclare une propriété.|[propriété](property-cpp-component-extensions.md)|
|**delegate**|Oui|Déclare un délégué.|[délégué (C++/CLI et C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|Oui|Déclare un événement.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Spécificateurs de substitution

Vous pouvez utiliser les mots clés suivants pour qualifier le comportement de substitution pour la dérivation. Bien que le mot clé **new** ne soit pas une extension de C++, il est répertorié ici car il peut être utilisé dans un autre contexte. Certains spécificateurs sont également valides pour la programmation native. Pour plus d'informations, voir [Procédure : déclarer des spécificateurs de substitution dans les compilations natives (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Oui|Indique que les fonctions ou classes sont abstraites.|[abstract](abstract-cpp-component-extensions.md)|
|**new**|Non|Indique qu'une fonction n'est pas une substitution d'une version de la classe de base.|[new (nouvel emplacement dans vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Oui|Indique qu'une méthode doit être une substitution d'une version de la classe de base.|[override](override-cpp-component-extensions.md)|
|**sealed**|Oui|Empêche les classes d'être utilisées comme classes de base.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Mots clés pour les génériques

Les mots clés suivants ont été ajoutés pour prendre en charge des types génériques. Pour plus d’informations, consultez la page [Génériques](generics-cpp-component-extensions.md).

|Mot clé|Contextuel|Objectif|
|-------------|-----------------------|-------------|
|**generic**|Non|Déclare un type générique.|
|**where**|Oui|Spécifie les contraintes appliquées à un paramètre de type générique.|

## <a name="miscellaneous-keywords"></a>Mots clés divers

Les mots clés suivants ont été ajoutés aux extensions C++.

|Mot clé|Contextuel|Objectif|Référence|
|-------------|-----------------------|-------------|---------------|
|**finally**|Oui|Indique le comportement de gestion des exceptions par défaut.|[Gestion des exceptions](exception-handling-cpp-component-extensions.md)|
|**for each, in**|Non|Énumère les éléments d’une collection.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Non|Alloue des types sur le tas récupéré par le garbage collector. À utiliser à la place de **new** et **delete**.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|Oui|Alloue un type Windows Runtime. À utiliser à la place de **new** et **delete**.|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Oui|Indique qu’un membre peut uniquement être initialisé lors de la déclaration ou dans un constructeur statique.|[initonly (C++-CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Oui|Crée une variable littérale.|[literal](literal-cpp-component-extensions.md)|
|**nullptr**|Non|Indique qu'un handle ou pointeur ne pointe pas vers un objet.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Constructions de modèle

Les constructions de langage suivantes sont implémentées comme modèles, plutôt que comme mots clés. Si vous spécifiez l'option de compilateur `/ZW`, elles sont définies dans l'espace de noms `lang`. Si vous spécifiez l'option de compilateur `/clr`, elles sont définies dans l'espace de noms `cli`.

|Mot clé|Objectif|Référence|
|-------------|-------------|---------------|
|**array**|Déclare un tableau.|[Tableaux](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(CLR uniquement) Pointe vers des données dans un type de référence.|[interior_ptr (C++-CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(CLR uniquement) Pointe vers des types de référence CLR pour supprimer temporairement le système de garbage collection.|[pin_ptr (C++-CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Détermine et exécute la méthode de casting optimale pour un type de runtime.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**typeid**|(CLR uniquement) Récupère un objet <xref:System.Type?displayProperty=fullName> qui décrit le type ou l'objet donné.|[typeid](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Déclarateurs

Les déclarateurs de type suivants demandent au runtime de gérer automatiquement la durée de vie et la suppression des objets alloués.

|Opérateur|Objectif|Référence|
|--------------|-------------|---------------|
|`^`|Déclare un handle à un objet ; autrement dit, un pointeur vers un objet Windows Runtime ou CLR qui est automatiquement supprimé quand il n’est plus utilisable.|[Handle sur l'opérateur Object (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Déclare une référence de suivi ; autrement dit, une référence vers un objet Windows Runtime ou CLR qui est automatiquement supprimé quand il n’est plus utilisable.|[Opérateur de référence de suivi](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Constructions supplémentaires et rubriques connexes

Cette section répertorie les constructions de programmation supplémentaires, ainsi que les rubriques qui se rapportent au CLR.

|Rubrique|Description|
|-----------|-----------------|
|[__identifier (C++-CLI)](identifier-cpp-cli.md)|(Windows Runtime et CLR) Permet d’utiliser des mots clés en tant qu’identificateurs.|
|[Listes d’arguments de variable (...) (C++-CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime et CLR) Permet à une fonction de prendre un nombre variable d’arguments.|
|[Équivalents .NET Framework des types natifs C++ (C++-CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Répertorie les types CLR qui sont utilisés à la place des types intégraux C++.|
|modificateur [appdomain](../cpp/appdomain.md) **__declspec** modifier|Modificateur **__declspec** qui impose que des variables statiques et globales existent par appdomain.|
|[Casts de style C avec /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|Décrit comment les casts de style C sont interprétées.|
|Convention d’appel [__clrcall](../cpp/clrcall.md)|Indique la convention d’appel conforme au CLR.|
|`__cplusplus_cli`|[Macros prédéfinies](../preprocessor/predefined-macros.md)|
|[Attributs personnalisés](user-defined-attributes-cpp-component-extensions.md)|Décrit comment définir vos propres attributs CLR.|
|[Gestion des exceptions](exception-handling-cpp-component-extensions.md)|Fournit une vue d'ensemble de la gestion des exceptions.|
|[Substitutions explicites](explicit-overrides-cpp-component-extensions.md)|Montre comment les fonctions membres peuvent substituer les membres arbitraires.|
|[Assemblys friend (C++)](../dotnet/friend-assemblies-cpp.md)|Explique comment un assembly client peut accéder à tous les types dans un composant d'assembly.|
|[Boxing](boxing-cpp-component-extensions.md)|Montre les conditions dans lesquelles les types de valeur sont boxed.|
|[Prise en charge du compilateur pour les Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md)|Explique comment détecter les caractéristiques des types au moment de la compilation.|
|Pragmas [managés, non managés](../preprocessor/managed-unmanaged.md)|Montre comment les fonctions managées et non managées peuvent coexister dans le même module.|
|Modificateur [process](../cpp/process.md) **__declspec**|Modificateur **__declspec** qui impose que des variables statiques et globales existent par process.|
|[Réflexion (C++-CLI)](../dotnet/reflection-cpp-cli.md)|Montre la version CLR des informations de type au moment de l'exécution.|
|[String](string-cpp-component-extensions.md)|Décrit la conversion du compilateur des littéraux de chaîne en <xref:System.String>.|
|[Transfert de type (C++-CLI)](type-forwarding-cpp-cli.md)|Permet le déplacement d'un type dans un assembly d'expédition vers un autre assembly afin que le code client n'ait pas besoin d'être recompilé.|
|[Attributs définis par l'utilisateur](user-defined-attributes-cpp-component-extensions.md)|Montre les attributs définis par l'utilisateur.|
|[Directive #using](../preprocessor/hash-using-directive-cpp.md)|Importe des assemblys externes.|
|[Documentation XML](../build/reference/xml-documentation-visual-cpp.md)|Explique la documentation du code XML à l’aide de [/doc (Traiter les commentaires de documentation) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md).|

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)