---
title: '#import, directive (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332066"
---
# <a name="import-directive-c"></a>directive #import (C)

**Section spécifique à C++**

Utilisé pour incorporer les informations d'une bibliothèque de types. Le contenu de la bibliothèque de types est converti en classes C++, qui décrivent principalement les interfaces COM.

## <a name="syntax"></a>Syntaxe

> **#import** " nom de \[*fichier*" *attributs*]
> \< **#import** *attributs* *du nom de*> \[fichier ]

### <a name="parameters"></a>Paramètres

*Fichier*\
Spécifie la bibliothèque de types à importer. Le *nom de fichier* peut être l’un des types suivants :

- Nom d'un fichier qui contient une bibliothèque de types, par exemple un fichier .olb, .tlb ou .dll. Le mot `file:`clé, , peut précéder chaque nom de fichier.

- Progid d'un contrôle dans la bibliothèque de types. Le mot `progid:`clé, , peut précéder chaque progid. Par exemple :

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Pour en savoir plus sur les progids, voir [Specifying the Localization ID and Version Number](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Lorsque vous utilisez un compilateur croisé 32 bits sur un système d’exploitation 64 bits, le compilateur ne peut lire que la ruche de registre 32 bits. Vous pouvez utiliser le compilateur 64 bits natif pour générer et inscrire une bibliothèque de types 64 bits.

- ID de bibliothèque de la bibliothèque de types. Le mot `libid:`clé, , peut précéder chaque ID de bibliothèque. Par exemple :

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Si vous ne `version` spécifiez pas `lcid`ou `libid:`, les [règles](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) appliquées à `progid:` sont également appliquées à .

- Fichier exécutable (.exe).

- Un fichier de bibliothèque (.dll) contenant une ressource de bibliothèque type (comme un .ocx).

- Document composite contenant une bibliothèque de types.

- Tout autre format de fichier qui peut être compris par l’API **LoadTypeLib.**

*Attributs*\
Un ou plusieurs [attributs #import](#_predir_the_23import_directive_import_attributes). Sépare les attributs par un espace ou une virgule. Par exemple :

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- ou -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Notes

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>Commande de recherche pour le nom de fichier

*nom de fichier* est optionnellement précédé par une spécification d’annuaire. Le nom de fichier doit désigner un fichier existant. La différence entre les deux formes de syntaxe provient de l'ordre dans lequel le préprocesseur recherche les fichiers de bibliothèque de type lorsque le chemin d'accès est spécifié de manière incomplète.

|Forme syntaxique|Action|
|-----------------|------------|
|Forme avec guillemets|Demande au préprocesseur de rechercher les fichiers de bibliothèque de type **#import** d’abord dans l’annuaire du fichier qui`#include`contient la #import déclaration, puis dans les répertoires de tous les fichiers comprennent ( ) ce fichier. Le préprocesseur explore ensuite les chemins d’accès spécifiés ci-dessous.|
|Forme avec crochets pointus|Indique au préprocesseur de rechercher les fichiers bibliothèques de types en utilisant les chemins d’accès suivants :<br /><br /> 1. `PATH` La liste des trajectoires variables de l’environnement<br />2. `LIB` La liste des trajectoires variables de l’environnement<br />3. Le chemin spécifié par l’option de compilateur [/I,](../build/reference/i-additional-include-directories.md) sauf que le compilateur est à la recherche d’une bibliothèque de type qui a été référencée à partir d’une autre bibliothèque de type avec [l’attribut no_registry.](../preprocessor/no-registry.md)|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Spécifier l’ID de localisation et le numéro de version

Lorsque vous spécifiez un progid, vous pouvez également spécifier l'ID de localisation et le numéro de version du progid. Par exemple :

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Si vous ne spécifiez pas une pièce d’identité de localisation, un progide est choisi selon les règles suivantes :

- S’il n’y a qu’une seule pièce d’identité de localisation, celle-ci est utilisée.

- S’il y a plus d’un ID de localisation, le premier avec la version numéro 0, 9 ou 409 est utilisé.

- S’il y a plus d’une pièce d’identité de localisation et qu’aucun d’entre eux n’est 0, 9 ou 409, le dernier est utilisé.

- Si vous ne spécifiez pas un numéro de version, la version la plus récente est utilisée.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>Fichiers d’en-tête créés par importation

**#import** crée deux fichiers d’en-tête qui reconstruisent le contenu de la bibliothèque de type dans le code source C. Le fichier d’en-tête principal est similaire à celui produit par le compilateur Microsoft Interface Definition Language (MIDL), mais avec du code et des données générés par compilateur supplémentaires. Le [fichier d’en-tête principal](#_predir_the_primary_type_library_header_file) a le même nom de base que la bibliothèque de type, plus un . Extension TLH. Le fichier d’en-tête secondaire possède le même nom de base que la bibliothèque de types, avec une extension .TLI. Il contient les implémentations des fonctions membres générées par le compilateur, et est inclus (`#include`) dans le fichier d'en-tête principal.

Si l’importation d’une propriété `byref` dispinterface qui utilise des paramètres, **#import** ne génère pas un [relevé de __declspec (propriété)](../cpp/property-cpp.md) pour la fonction.

Les deux fichiers d’en-tête sont placés dans l’annuaire de sortie spécifié par l’option [/Fo (fichier d’objets nominaux).](../build/reference/fo-object-file-name.md) Ils sont ensuite lus et compilés par le compilateur `#include` comme si le fichier d’en-tête principal a été nommé par une directive.

Les optimisations compilateur suivantes sont livrés avec la directive **#import** :

- Le fichier d'en-tête, une fois créé, porte le même horodatage que la bibliothèque de types.

- Lorsque **#import** est traitée, le compilateur vérifie d’abord si l’en-tête existe et est à jour. Si oui, alors il n’a pas besoin d’être recréé.

La directive **#import** participe également à une reconstruction minimale et peut être placée dans un fichier d’en-tête précomposé.  Pour plus d’informations, voir [Créer des fichiers d’en-tête précompilés](../build/creating-precompiled-header-files.md).

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>Fichier d’en-tête de bibliothèque de type primaire

Le fichier d'en-tête principal de bibliothèque de types se compose de sept sections :

- Zones fixes de titre : se composent des commentaires, de l'instruction `#include` pour COMDEF.H (qui définit des macros standard utilisées dans l'en-tête) et d'autres informations de configuration diverses.

- Références anticipées et typedefs : se composent de déclarations de structure comme `struct IMyInterface` et de définitions de types (typedefs).

- Déclarations pointeurs intelligents: `_com_ptr_t` La classe de modèle est un pointeur intelligent. Il encapsule les pointeurs d’interface, `AddRef`et `Release`élimine `QueryInterface` le besoin d’appeler, , et fonctionne. Il cache également `CoCreateInstance` l’appel lors de la création d’un nouvel objet COM. Cette section utilise `_COM_SMARTPTR_TYPEDEF` l’énoncé macro pour établir des types d’interfaces COM comme des spécialisations de modèle de la classe de modèle [de _com_ptr_t.](../cpp/com-ptr-t-class.md) Par exemple, `IMyInterface`pour l’interface , le . Le fichier TLH contiendra :

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   ce que le compilateur développe en :

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Le type `IMyInterfacePtr` peut alors être utilisé à la place du pointeur d'interface brut `IMyInterface*`. Par conséquent, il n’est pas `IUnknown` nécessaire d’appeler les différentes fonctions des membres

- Déclarations Typeinfo: Se compose principalement de définitions de classe et `ITypeLib:GetTypeInfo`d’autres éléments exposant les différents éléments typeinfo retourné par . Dans cette section, chaque typeinfo de la bibliothèque de types est répercuté dans l'en-tête en fonction des informations de `TYPEKIND`.

- Ancienne définition de GUID facultative : contient les initialisations des constantes GUID nommées. Ces noms ont `CLSID_CoClass` `IID_Interface`la forme et , similaire à ceux générés par le compilateur MIDL.

- Instruction `#include` pour l'en-tête de bibliothèque de types secondaires.

- Zones fixes de pied de page : incluent actuellement `#pragma pack(pop)`.

Toutes les sections, à l’exception de la plaque chauffante de tête et de `library` la section de la chaudière de pied, sont enfermées dans un espace nominant dont le nom est spécifié par la déclaration dans le fichier IDL original. Vous pouvez utiliser les noms de l’en-tête de la bibliothèque de type par une qualification explicite en utilisant le nom namespace. Ou, vous pouvez inclure la déclaration suivante:

```cpp
using namespace MyLib;
```

immédiatement après la **déclaration #import** dans le code source.

L’espace nom peut être supprimé en utilisant [l’attribut no_namespace)](no-namespace.md)de la directive **#import.** Toutefois, la suppression de l'espace de noms peut entraîner des collisions de noms. L’espace de nom peut également être renommé par l’attribut [rename_namespace.](rename-namespace.md)

Le compilateur offre le chemin complet à toute dépendance de bibliothèque de type exigé par la bibliothèque de type qu’il traite actuellement. Le chemin d’accès est écrit, sous forme de commentaires, dans l’en-tête de bibliothèque de types (.TLH) que le compilateur génère pour chaque bibliothèque de types traitée.

Si une bibliothèque de types inclut des références aux types définis dans d'autres bibliothèques de types, le fichier .TLH inclura des commentaires du type suivant :

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Le nom de fichier réel dans le **commentaire #import** est le chemin complet de la bibliothèque de type cross-referenced, tel que stocké dans le registre. Si vous rencontrez des erreurs qui sont causées par des définitions de type manquant, vérifiez les commentaires à la tête de la . TLH pour voir quelles bibliothèques de type dépendant peuvent avoir besoin d’être importées en premier. Les erreurs possibles sont des erreurs de syntaxe, par exemple C2143, C2146, C2321, C2501 (decl-specifiers absents) ou C2433 (« inline » non autorisé dans la déclaration de données) lors de la compilation du fichier .TLI.

Pour résoudre les erreurs de dépendance, déterminer lequel des commentaires sur la dépendance n’est pas autrement prévu par les en-têtes du système, puis fournir une directive **#import** à un moment donné avant la directive **#import** de la bibliothèque de type dépendant.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import attributs

**#import** peut inclure en option un ou plusieurs attributs. Ces attributs demandent au compilateur de modifier le contenu des en-têtes de bibliothèque de types. Un symbole de**\\**barre oblique inverse ( ) peut être utilisé pour inclure des lignes supplémentaires dans une seule **déclaration #import.** Par exemple :

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Pour plus d’informations, voir [#import attributs](../preprocessor/hash-import-attributes-cpp.md).

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)\
[Support Compiler COM](../cpp/compiler-com-support.md)
