---
title: Aide-mémoire (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b3ee46b2be08992fa3254edfbf2423b80dcabb1
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102115"
---
# <a name="quick-reference-ccx"></a>Aide-mémoire (C++/CX)

Le Runtime Windows prend en charge les applications Universal Windows Platform (UWP) qui s’exécutent uniquement dans un environnement de système d’exploitation fiable, utilisent les fonctions autorisées, les types de données et les appareils et sont distribuées via le Microsoft Store. C++ / c++ / CX simplifient l’écriture d’applications pour l’exécution de Windows. Cet article est une référence rapide ; Pour obtenir une documentation plus complète, consultez [système de Type](../cppcx/type-system-c-cx.md).

Lorsque vous générez sur la ligne de commande, utilisez le **/ZW** option du compilateur pour générer une application UWP ou un composant Windows Runtime. Pour accéder aux déclarations de Windows Runtime, qui sont définies dans les fichiers de métadonnées (.winmd) Windows Runtime, spécifiez la `#using` directive ou **/FU** option du compilateur. Lorsque vous créez un projet pour une application UWP, Visual Studio par défaut définit ces options et ajoute des références à toutes les bibliothèques Windows Runtime.

## <a name="quick-reference"></a>Aide-mémoire

|Concept|C++ standard|C++/CX|Notes|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Types fondamentaux|Types fondamentaux C++|C++ / c++ / types fondamentaux CX qui implémentent les types fondamentaux qui sont définis dans le Runtime de Windows.|Le `default` contient de l’espace de noms C++ / c++ / CX types fondamentaux intégrés. Le compilateur mappe implicitement C + c++ / types fondamentaux de CX aux types C++ standard.<br /><br /> Le `Platform` famille d’espaces de noms contient des types qui implémentent les types fondamentaux de Windows Runtime.|
||`bool`|`bool`|Valeur booléenne de 8 bits.|
||`__wchar_t`|`char16`|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|Entier signé 16 bits.<br /><br /> Entier non signé 16 bits.|
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|Entier signé 32 bits.<br /><br /> Entier non signé 32 bits.|
||`long long` ou `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|Entier signé 64 bits.<br /><br /> Entier 64 bits non signé.|
||`float, double`|`float32, float64`|Nombre à virgule flottante IEEE 754 32 bits ou 64 bits.|
||`enum {}`|`enum class {}`<br /><br /> - ou -<br /><br /> `enum struct {}`|Énumération de 32 bits.|
||(Non applicable)|`Platform::Guid`|Valeur non numérique de 128 bits (un GUID) dans l'espace de noms `Platform` .|
||`std::time_get`|`Windows::Foundation::DateTime`|Structure date-time.|
||(Non applicable)|`Windows::Foundation::TimeSpan`|Structure timespan.|
||(Non applicable)|`Platform::Object^`|L’objet de base contenant des références dans la vue C++ du système de type Windows Runtime.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` est une séquence de caractères Unicode représentant du texte, immuable et faisant l'objet d'un décompte de références.|
|Pointeur|Pointeur vers un objet (`*`) :<br /><br /> `std::shared_ptr`|Handle-to-object (`^`, prononcé « chapeau ») :<br /><br /> *Identificateur T^*|Toutes les classes Windows Runtime sont déclarés à l’aide du modificateur handle-to-object. Les membres de l'objet sont accessibles à l'aide de l'opérateur class-member-access flèche (`->`).<br /><br /> Le modificateur hat signifie « pointeur vers un objet Windows Runtime qui est automatiquement référence comptée. » Plus précisément, handle-to-object déclare que le compilateur doit insérer du code pour gérer automatiquement le décompte de références de l'objet, et supprime l'objet si le décompte de références atteint zéro.|
|Référence|Référence à un objet (`&`) :<br /><br /> *T* `&` *identifier*|Suivi des références (`%`) :<br /><br /> *T* `%` *identifier*|Seul Windows Runtime, les types peuvent être déclarés à l’aide du suivi de référence modificateur. Les membres de l'objet sont accessibles à l'aide de l'opérateur class-member-access point (`.`).<br /><br /> La référence de suivi signifie « une référence à un objet Windows Runtime qui est automatiquement référence comptée. » Plus précisément, une référence de suivi déclare que le compilateur doit insérer du code pour gérer automatiquement le décompte de références de l'objet, et supprime l'objet si le décompte de références atteint zéro.|
|déclaration de type dynamique|`new`|`ref new`|Alloue un objet Windows Runtime, puis retourne un handle à cet objet.|
|gestion de la durée de vie d'un objet|`delete` *identifier*<br /><br /> `delete[]`  *identifier*|(Appelle le destructeur.)|La durée de vie est déterminée par le décompte de références. Un appel de delete appelle le destructeur mais ne libère pas lui-même la mémoire.|
|Déclaration de tableau|*Identificateur T* `[]`<br /><br /> `std::array` *identifier*|`Array<` *T* `^>^` *identifier* `(` *size* `)`<br /><br /> - ou -<br /><br /> `WriteOnlyArray<` *T* `^>`  *identifier* `(` *size* `)`|Déclare un tableau modifiable unidimensionnel ou un tableau de type T^ en écriture seule. Le tableau lui-même est également un objet faisant l'objet d'un décompte de références qui doit être déclaré à l'aide du modificateur handle-to-object.<br /><br /> (Les déclarations de tableau utilisent une classe d'en-tête de modèle qui se trouve dans l'espace de noms `Platform` .)|
|déclaration de classe|`class`  *identifier* `{}`<br /><br /> `struct` *identifier* `{}`|`ref class` *identifier* `{}`<br /><br /> `ref struct` *identifier* `{}`|Déclare une classe d'exécution ayant un accès privé par défaut.<br /><br /> Déclare une classe d'exécution ayant un accès public par défaut.|
|déclarations de structure|`struct` *identifier* `{}`<br /><br /> (qui est une structure POD (Plain Old Data Structure)|`value class` *identifier* `{}`<br /><br /> `value struct` *identifier* `{}`|Déclare une structure POD ayant un accès privé par défaut.<br /><br /> Une classe de valeur peut être représentée dans les métadonnées Windows, mais une classe C++ standard ne le peut pas.<br /><br /> Déclare une structure POD ayant un accès public par défaut.<br /><br /> Une structure de valeur peut être représentée dans les métadonnées Windows, mais une structure C++ standard ne le peut pas.|
|déclaration d'interface|classe abstraite qui contient uniquement des fonctions virtuelles pures.|`interface class` *identifier* `{}`<br /><br /> `interface struct` *identifier* `{}`|Déclare une interface ayant un accès privé par défaut.<br /><br /> Déclare une interface ayant un accès public par défaut.|
|délégué|`std::function`|`public delegate` *return-type* *delegate-type-identifier* `(` *[ parameters ]* `);`|Déclare un objet qui peut être appelé comme un appel de fonction.|
|événement|(Non applicable)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this`*[, parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> - ou -<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> - ou -<br /><br /> `auto` *identificateur de jeton* = *obj*. *identificateur d’événement*`::add(`*identificateur de délégué*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> - ou -<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|Déclare un objet d'événement, qui stocke une collection de gestionnaires d'événements (délégués) qui sont appelés lorsqu'un événement se produit.<br /><br /> Crée un gestionnaire d'événements.<br /><br /> Ajoute un gestionnaire d'événements.<br /><br /> L’ajout d’un gestionnaire d’événements retourne un jeton d’événement (*token-identifier*). Si vous prévoyez de supprimer explicitement le gestionnaire d'événements, vous devez enregistrer le jeton d'événement pour l'utiliser ultérieurement.<br /><br /> Supprime un gestionnaire d'événements.<br /><br /> Pour supprimer un gestionnaire d'événements, vous devez spécifier le jeton d'événement que vous avez enregistré lorsque le gestionnaire d'événements a été ajouté.|
|propriété|(Non applicable)|`property` *T* *identifier*;<br /><br /> `property` *T* *identifier* `[` *index* `];`<br /><br /> `property` *T* `default[` *index* `];`|Déclare qu'une fonction membre de classe ou d'objet est accessible en utilisant la même syntaxe qui est utilisée pour accéder à des données membres ou à un élément de tableau indexé.<br /><br /> Déclare une propriété sur une fonction membre de classe ou d'objet.<br /><br /> Déclare une propriété indexée sur une fonction membre d'objet.<br /><br /> Déclare une propriété indexée sur une fonction membre de classe.|
|Types paramétrables|modèles|`generic <typename` *T* `> interface class` *identifier* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|Déclare une classe d'interface paramétrée.<br /><br /> Déclare un délégué paramétré.|
|Types valeur Nullable|`boost::optional<T>`|[Platform::IBox \<T >](../cppcx/platform-ibox-interface.md)|Permet aux variables des types scalaires et des structs value d'avoir la valeur `nullptr`.|

## <a name="see-also"></a>Voir aussi

[Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)