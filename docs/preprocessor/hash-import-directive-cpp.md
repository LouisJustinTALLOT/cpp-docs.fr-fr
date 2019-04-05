---
title: '#Importer la Directive (C++)'
ms.date: 03/27/2019
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
ms.openlocfilehash: 98a0f9f66fb209bb41215fc1e86a9682a4fed023
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031983"
---
# <a name="import-directive-c"></a>#import, directive (C++)

**Section spécifique à C++**

Utilisé pour incorporer les informations d'une bibliothèque de types. Le contenu de la bibliothèque de types est converti en classes C++, qui décrivent principalement les interfaces COM.

## <a name="syntax"></a>Syntaxe

```
#import "filename" [attributes]
#import <filename> [attributes]
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Spécifie la bibliothèque de types à importer. *nom de fichier* peut prendre l’une des opérations suivantes :

- Nom d'un fichier qui contient une bibliothèque de types, par exemple un fichier .olb, .tlb ou .dll. Le mot clé, **fichier :**, peut précéder chaque nom de fichier.

- Progid d'un contrôle dans la bibliothèque de types. Le mot clé, **progid :**, peut précéder chaque progid. Exemple :

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Pour plus d’informations sur les ProgID, consultez [spécifiant l’ID de localisation et le numéro de Version](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Notez que lorsque vous compilez avec un compilateur croisé sur un système d'exploitation 64 bits, le compilateur ne peut lire que la ruche du Registre 32 bits. Vous pouvez utiliser le compilateur 64 bits natif pour générer et inscrire une bibliothèque de types 64 bits.

- ID de bibliothèque de la bibliothèque de types. Le mot clé, **libid :**, peut précéder chaque ID de bibliothèque. Exemple :

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Si vous ne spécifiez pas de version ou le lcid, les [règles](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) qui sont appliqués à **progid :** sont également appliquées à **libid :**.

- Fichier exécutable (.exe).

- Fichier de bibliothèque (.dll) contenant une ressource de bibliothèque de types (telle que .ocx).

- Document composite contenant une bibliothèque de types.

- Tout autre format de fichier qui peut être reconnu par le **LoadTypeLib** API.

*attributs*<br/>
Un ou plusieurs [attributs #import](#_predir_the_23import_directive_import_attributes). Sépare les attributs par un espace ou une virgule. Exemple :

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- ou -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Notes

## <a name="_predir_the_23import_directive_searchorderforfilename"></a> Ordre de recherche de nom de fichier

*nom de fichier* est éventuellement précédé d’une spécification de répertoire. Le nom de fichier doit désigner un fichier existant. La différence entre les deux formes de syntaxe provient de l'ordre dans lequel le préprocesseur recherche les fichiers de bibliothèque de type lorsque le chemin d'accès est spécifié de manière incomplète.

|Forme syntaxique|Action|
|-----------------|------------|
|Forme avec guillemets|Indique au préprocesseur de rechercher des fichiers de bibliothèque de type dans le répertoire du fichier qui contient le **#import** instruction, puis dans les répertoires de fichiers qui incluent (`#include`) ce fichier. Le préprocesseur explore ensuite les chemins d’accès spécifiés ci-dessous.|
|Forme avec crochets pointus|Indique au préprocesseur de rechercher les fichiers bibliothèques de types en utilisant les chemins d’accès suivants :<br /><br /> 1.  Le `PATH` liste variable de chemin d’accès d’environnement<br />2.  Le `LIB` liste variable de chemin d’accès d’environnement<br />3.  Le chemin d’accès spécifié par le /I (autres répertoires include) option du compilateur, sauf si le compilateur recherche une bibliothèque de types référencée à partir d’une autre bibliothèque de types avec le [no_registry](../preprocessor/no-registry.md) attribut.|

##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> En spécifiant l’ID de localisation et le numéro de Version

Lorsque vous spécifiez un progid, vous pouvez également spécifier l'ID de localisation et le numéro de version du progid. Exemple :

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Si vous ne spécifiez pas d'ID de localisation, un progid est choisi selon les règles suivantes :

- S'il existe un seul ID de localisation, celui-ci est utilisé.

- S'il existe plusieurs ID de localisation, le premier ayant le numéro de version 0, 9 ou 409 est utilisé.

- S'il existe plusieurs ID de localisation et qu'aucun d'entre eux n'est 0, 9 ou 409, le dernier est utilisé.

- Si vous ne spécifiez pas de numéro de version, la version la plus récente est utilisée.

##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> Fichiers d’en-tête créés par l’importation

**#import** crée deux fichiers d’en-tête qui reconstruisent le contenu de bibliothèque de type dans le code source C++. Le fichier d'en-tête principal est similaire à celui produit par le compilateur MIDL (Microsoft Interface Definition Langage), mais avec un code et des données supplémentaires générés par le compilateur. Le [fichier d’en-tête principal](#_predir_the_primary_type_library_header_file) a le même nom que la bibliothèque de types, plus un. Extension TLH. Le fichier d’en-tête secondaire possède le même nom de base que la bibliothèque de types, avec une extension .TLI. Il contient les implémentations des fonctions membres générées par le compilateur, et est inclus (`#include`) dans le fichier d'en-tête principal.

Si vous importez une propriété dispinterface qui utilise des paramètres byref, #import ne générera pas __declspec ([propriété](../cpp/property-cpp.md)) instruction pour la fonction.

Les deux fichiers d'en-tête sont placés dans le répertoire de sortie spécifié par l'option /Fo (Nom du fichier objet). Ils sont ensuite lus et compilés par le compilateur comme si le fichier d'en-tête principal était nommé par une directive `#include`.

Les optimisations du compilateur suivantes sont fournis avec le **#import** directive :

- Le fichier d'en-tête, une fois créé, porte le même horodatage que la bibliothèque de types.

- Lorsque **#import** est traité, le compilateur vérifie d’abord si l’en-tête existe et qu’il est à jour. Si oui, il est inutile de le recréer.

Le **#import** directive également participe à la régénération minimale et peut être placée dans un fichier d’en-tête précompilé. Consultez [création de fichiers d’en-tête précompilé](../build/creating-precompiled-header-files.md) pour plus d’informations.

###  <a name="_predir_the_primary_type_library_header_file"></a> Fichier d’en-tête de bibliothèque de Type principal
Le fichier d'en-tête principal de bibliothèque de types se compose de sept sections :

- Zones fixes de titre : Se compose de commentaires, `#include` instruction pour COMDEF. H (qui définit des macros standard utilisées dans l’en-tête) et d’autres informations de configuration diverses.

- Références anticipées et typedefs : Se compose des déclarations de structure comme `struct IMyInterface` et typedefs.

- Déclarations de pointeur intelligent : La classe de modèle `_com_ptr_t` est une implémentation de pointeur intelligent qui encapsule des pointeurs d’interface et élimine la nécessité d’appeler `AddRef`, `Release`, `QueryInterface` fonctions. En outre, elle masque l'appel de `CoCreateInstance` en créant un nouvel objet COM. Cette section utilise l’instruction macro `_COM_SMARTPTR_TYPEDEF` pour établir les typedefs des interfaces COM pour être des spécialisations de modèle de la [_com_ptr_t](../cpp/com-ptr-t-class.md) classe de modèle. Par exemple, pour l’interface `IMyInterface`, le. Les fichiers TLH contiendra :

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   ce que le compilateur développe en :

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Le type `IMyInterfacePtr` peut alors être utilisé à la place du pointeur d'interface brut `IMyInterface*`. Par conséquent, il n’est pas nécessaire d’appeler les différentes `IUnknown` fonctions membres

- Déclarations de TypeInfo : Se compose principalement de définitions de classe et d’autres éléments exposant les différents éléments de typeinfo retournés par `ITypeLib:GetTypeInfo`. Dans cette section, chaque typeinfo de la bibliothèque de types est répercuté dans l'en-tête en fonction des informations de `TYPEKIND`.

- Définition de GUID facultative ancienne : Contient les initialisations des constantes GUID nommées. Il s’agit des noms au format `CLSID_CoClass` et `IID_Interface`, semblables à ceux générés par le compilateur MIDL.

- `#include` instruction de l’en-tête de bibliothèque de type secondaire.

- Réutilisable de pied de page : Inclut actuellement `#pragma pack(pop)`.

Toutes les sections, à l’exception de la section de code réutilisable de titre réutilisable et un pied de page, sont placées dans un espace de noms portant le nom spécifié par le `library` instruction dans le fichier IDL d’origine. Vous pouvez utiliser les noms de l'en-tête de la bibliothèque de types en spécifiant une qualification explicite avec le nom de l'espace de noms ou en incluant l'instruction suivante :

```cpp
using namespace MyLib;
```

immédiatement après le **#import** instruction dans le code source.

L’espace de noms peut être supprimée à l’aide de la [no_namespace](no-namespace.md)) attribut de la **#import** directive. Toutefois, la suppression de l'espace de noms peut entraîner des collisions de noms. L’espace de noms peut également être renommé par la [rename_namespace](rename-namespace.md) attribut.

Le compilateur fournit le chemin d’accès complet aux dépendances de bibliothèque de types requises par la bibliothèque de types qu’il traite actuellement. Le chemin d’accès est écrit, sous forme de commentaires, dans l’en-tête de bibliothèque de types (.TLH) que le compilateur génère pour chaque bibliothèque de types traitée.

Si une bibliothèque de types inclut des références aux types définis dans d'autres bibliothèques de types, le fichier .TLH inclura des commentaires du type suivant :

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Le nom de fichier réel dans le **#import** commentaire est le chemin d’accès complet de la bibliothèque de types à références croisées, tel que stocké dans le Registre. Si vous rencontrez des erreurs dues à des définitions de type manquantes, vérifiez les commentaires au début du .TLH pour voir quelles bibliothèques de types dépendants doivent être importées en premier. Les erreurs possibles sont des erreurs de syntaxe, par exemple C2143, C2146, C2321, C2501 (decl-specifiers absents) ou C2433 (« inline » non autorisé dans la déclaration de données) lors de la compilation du fichier .TLI.

Vous devez déterminer quel de la dépendance commentaires ne sont pas fournis par les en-têtes systèmes et ensuite fournissent un **#import** directive à un moment donné avant le **#import** directive du dépendant bibliothèque de types pour résoudre les erreurs.

## <a name="_predir_the_23import_directive_import_attributes"></a> attributs #import

**#import** peut éventuellement inclure un ou plusieurs attributs. Ces attributs demandent au compilateur de modifier le contenu des en-têtes de bibliothèque de types. Une barre oblique inverse (**\\**) symbole peut être utilisé pour inclure des lignes supplémentaires dans un seul **#import** instruction. Exemple :

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Pour plus d’informations, consultez [attributs #import](../preprocessor/hash-import-attributes-cpp.md).

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)<br/>
[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)