---
title: Aide-mémoire (C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 6effcaec6a619bdd674dcae3bf4092fe82404d08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214969"
---
# <a name="quick-reference-ccx"></a>Aide-mémoire (C++/CX)

Le Windows Runtime prend en charge les applications plateforme Windows universelle (UWP) qui s’exécutent uniquement dans un environnement de système d’exploitation fiable, utilisent des fonctions, des types de données et des appareils autorisés, et sont distribués via le Microsoft Store. Le C++/CX simplifie l’écriture d’applications pour le Windows Runtime. Cet article est une référence rapide. pour obtenir une documentation plus complète, consultez [système de type](../cppcx/type-system-c-cx.md).

Quand vous générez sur la ligne de commande, utilisez l’option du compilateur **/ZW** pour générer une application UWP ou Windows Runtime composant. Pour accéder à Windows Runtime déclarations, qui sont définies dans les fichiers de métadonnées Windows Runtime (. winmd), spécifiez la `#using` directive ou l’option de compilateur **/Fu** . Lorsque vous créez un projet pour une application UWP, Visual Studio définit par défaut ces options et ajoute des références à toutes les bibliothèques de Windows Runtime.

## <a name="quick-reference"></a>Aide-mémoire

|Concept|C++ standard|C++/CX|Notes|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Types fondamentaux|Types fondamentaux C++|Les types fondamentaux C++/CX qui implémentent les types fondamentaux définis dans le Windows Runtime.|L' `default` espace de noms contient des types fondamentaux intégrés à C++/CX. Le compilateur mappe implicitement les types fondamentaux C++/CX aux types C++ standard.<br /><br /> La `Platform` famille d’espaces de noms contient des types qui implémentent des types de Windows Runtime fondamentaux.|
||**`bool`**|**`bool`**|Valeur booléenne de 8 bits.|
||**`wchar_t`**, **`char16_t`**|`char16`|Valeur non numérique 16 bits qui représente un point de code Unicode (UTF-16).|
||**`short`**<br /><br /> **`unsigned short`**|`int16`<br /><br /> `uint16`|Entier signé 16 bits.<br /><br /> Entier non signé 16 bits.|
||**`int`**<br /><br /> **`unsigned int`**|**`int`**<br /><br /> `uint32`|Entier signé de 32 bits.<br /><br /> Entier non signé 32 bits.|
||**`long long`** ni**`__int64`**<br /><br /> **`unsigned long long`**|`int64`<br /><br /> `uint64`|Entier signé de 64 bits.<br /><br /> Entier non signé 64 bits.|
||**`float`**, **`double`**|`float32, float64`|Nombre à virgule flottante IEEE 754 32 bits ou 64 bits.|
||**`enum`**|**`enum class`**<br /><br /> -ou-<br /><br /> **`enum struct`**|Énumération de 32 bits.|
||(Non applicable)|`Platform::Guid`|Valeur non numérique de 128 bits (un GUID) dans l'espace de noms `Platform` .|
||`std::time_get`|`Windows::Foundation::DateTime`|Structure date-time.|
||(Non applicable)|`Windows::Foundation::TimeSpan`|Structure timespan.|
||(Non applicable)|`Platform::Object^`|Objet de base de référence compté dans la vue C++ du système de type Windows Runtime.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` est une séquence de caractères Unicode représentant du texte, immuable et faisant l'objet d'un décompte de références.|
|Pointeur|Pointeur vers un objet (`*`) :<br /><br /> `std::shared_ptr`|Handle-to-object (`^`, prononcé « chapeau ») :<br /><br /> *Identificateur T^*|Toutes les classes Windows Runtimees sont déclarées à l’aide du modificateur handle-to-Object. Les membres de l'objet sont accessibles à l'aide de l'opérateur class-member-access flèche (`->`).<br /><br /> Le modificateur de chapeau signifie « pointeur vers un objet Windows Runtime qui fait automatiquement l’objet d’un comptage des références ». Plus précisément, handle-to-object déclare que le compilateur doit insérer du code pour gérer automatiquement le décompte de références de l'objet, et supprime l'objet si le décompte de références atteint zéro.|
|Informations de référence|Référence à un objet (`&`) :<br /><br /> *T* `&` *identifier*|Suivi des références (`%`) :<br /><br /> *T* `%` *identifier*|Seuls les types de Windows Runtime peuvent être déclarés à l’aide du modificateur de référence de suivi. Les membres de l'objet sont accessibles à l'aide de l'opérateur class-member-access point (`.`).<br /><br /> La référence de suivi signifie « une référence à un objet Windows Runtime qui fait automatiquement l’objet d’un comptage des références ». Plus précisément, une référence de suivi déclare que le compilateur doit insérer du code pour gérer automatiquement le décompte de références de l'objet, et supprime l'objet si le décompte de références atteint zéro.|
|déclaration de type dynamique|`new`|`ref new`|Alloue un objet Windows Runtime, puis retourne un handle vers cet objet.|
|gestion de la durée de vie d'un objet|`delete`*identificateur*<br /><br /> `delete[]`  *identificateur*|(Appelle le destructeur.)|La durée de vie est déterminée par le décompte de références. Un appel de delete appelle le destructeur mais ne libère pas lui-même la mémoire.|
|Déclaration de tableau|*Identificateur T*`[]`<br /><br /> `std::array`*identificateur*|`Array<` *T* `^>^` *identifier* `(` *size* `)`<br /><br /> -ou-<br /><br /> `WriteOnlyArray<` *T* `^>`  *identifier* `(` *size* `)`|Déclare un tableau modifiable unidimensionnel ou un tableau de type T^ en écriture seule. Le tableau lui-même est également un objet faisant l'objet d'un décompte de références qui doit être déclaré à l'aide du modificateur handle-to-object.<br /><br /> (Les déclarations de tableau utilisent une classe d'en-tête de modèle qui se trouve dans l'espace de noms `Platform` .)|
|déclaration de classe|**`class`***identificateur*`{}`<br /><br /> **`struct`***identificateur*`{}`|**`ref class`***identificateur*`{}`<br /><br /> **`ref struct`***identificateur*`{}`|Déclare une classe d'exécution ayant un accès privé par défaut.<br /><br /> Déclare une classe d'exécution ayant un accès public par défaut.|
|déclarations de structure|**`struct`***identificateur*`{}`<br /><br /> (qui est une structure POD (Plain Old Data Structure)|**`value class`***identificateur*`{}`<br /><br /> **`value struct`***identificateur*`{}`|Déclare une structure POD ayant un accès privé par défaut.<br /><br /> Une classe de valeur peut être représentée dans les métadonnées Windows, mais une classe C++ standard ne le peut pas.<br /><br /> Déclare une structure POD ayant un accès public par défaut.<br /><br /> Une structure de valeur peut être représentée dans les métadonnées Windows, mais une structure C++ standard ne le peut pas.|
|déclaration d'interface|classe abstraite qui contient uniquement des fonctions virtuelles pures.|**`interface class`***identificateur*`{}`<br /><br /> **`interface struct`***identificateur*`{}`|Déclare une interface ayant un accès privé par défaut.<br /><br /> Déclare une interface ayant un accès public par défaut.|
|Délégué|`std::function`|`public delegate` *return-type* *delegate-type-identifier* `(` *[ parameters ]* `);`|Déclare un objet qui peut être appelé comme un appel de fonction.|
|Événement|(Non applicable)|**`event`***identificateur d’événement* d' *identificateur de type délégué*`;`<br /><br /> Delegate *-type-identifier* -Delegate- *ID*  =  `ref new` *delegate-type-identifier* `( this` *[, Parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> -ou-<br /><br /> `EventRegistrationToken`*identificateur*  =  de jeton *obj* `.` *identificateur* `+=` d’événement *identificateur délégué*`;`<br /><br /> -ou-<br /><br /> **`auto`***identificateur*  =  de jeton *obj*. *identificateur* `::add(` d’événement *identificateur délégué*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> -ou-<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|Déclare un objet d'événement, qui stocke une collection de gestionnaires d'événements (délégués) qui sont appelés lorsqu'un événement se produit.<br /><br /> Crée un gestionnaire d'événements.<br /><br /> Ajoute un gestionnaire d'événements.<br /><br /> L’ajout d’un gestionnaire d’événements retourne un jeton d’événement (*token-identifier*). Si vous prévoyez de supprimer explicitement le gestionnaire d'événements, vous devez enregistrer le jeton d'événement pour l'utiliser ultérieurement.<br /><br /> Supprime un gestionnaire d'événements.<br /><br /> Pour supprimer un gestionnaire d'événements, vous devez spécifier le jeton d'événement que vous avez enregistré lorsque le gestionnaire d'événements a été ajouté.|
|Propriété|(Non applicable)|**`property`***T* *Identificateur*T ;<br /><br /> **`property`***T* *identifier* `[` *Index* d’identificateur T`];`<br /><br /> **`property`***T* `default[` *Index* T`];`|Déclare qu'une fonction membre de classe ou d'objet est accessible en utilisant la même syntaxe qui est utilisée pour accéder à des données membres ou à un élément de tableau indexé.<br /><br /> Déclare une propriété sur une fonction membre de classe ou d'objet.<br /><br /> Déclare une propriété indexée sur une fonction membre d'objet.<br /><br /> Déclare une propriété indexée sur une fonction membre de classe.|
|Types paramétrables|modèles|`generic <typename`*T* `> interface class` *Identificateur* T`{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|Déclare une classe d'interface paramétrée.<br /><br /> Déclare un délégué paramétré.|
|Types valeur Nullable|`boost::optional<T>`|[Platform :: IBox\<T>](../cppcx/platform-ibox-interface.md)|Permet aux variables des types scalaires et des structs de valeur d’avoir la valeur **`nullptr`** .|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
