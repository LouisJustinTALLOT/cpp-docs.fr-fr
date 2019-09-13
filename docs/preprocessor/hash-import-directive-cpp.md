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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220263"
---
# <a name="import-directive-c"></a>#import directive (C++)

**C++Plus**

Utilisé pour incorporer les informations d'une bibliothèque de types. Le contenu de la bibliothèque de types est converti en classes C++, qui décrivent principalement les interfaces COM.

## <a name="syntax"></a>Syntaxe

> **#import** *attributs*« nom \[de*fichier*»] \
> **#import**> attributs de nom defichier\[] \<

### <a name="parameters"></a>Paramètres

*extension*\
Spécifie la bibliothèque de types à importer. Le *nom de fichier* peut être l’un des types suivants :

- Nom d'un fichier qui contient une bibliothèque de types, par exemple un fichier .olb, .tlb ou .dll. Le mot clé `file:`,, peut précéder chaque nom de fichier.

- Progid d'un contrôle dans la bibliothèque de types. Le mot clé `progid:`,, peut précéder chaque ProgID. Par exemple :

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Pour plus d’informations sur les ProgID, consultez [spécification de l’ID de localisation et du numéro de version](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber).

   Quand vous utilisez un compilateur croisé 32 bits sur un système d’exploitation 64 bits, le compilateur ne peut lire que la ruche de Registre 32 bits. Vous pouvez utiliser le compilateur 64 bits natif pour générer et inscrire une bibliothèque de types 64 bits.

- ID de bibliothèque de la bibliothèque de types. Le mot clé `libid:`,, peut précéder chaque ID de bibliothèque. Par exemple :

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   Si vous ne spécifiez pas `version` ou `lcid`, les [règles](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber) appliquées à `progid:` sont également appliquées à `libid:`.

- Fichier exécutable (.exe).

- Fichier de bibliothèque (. dll) contenant une ressource de bibliothèque de types (par exemple,. ocx).

- Document composite contenant une bibliothèque de types.

- Tout autre format de fichier pouvant être compris par l’API **LoadTypeLib** .

*attributs*\
Un ou plusieurs [attributs #import](#_predir_the_23import_directive_import_attributes). Sépare les attributs par un espace ou une virgule. Par exemple :

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\- ou -

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>Notes

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>Ordre de recherche du nom de fichier

le *nom de fichier* est éventuellement précédé d’une spécification de répertoire. Le nom de fichier doit désigner un fichier existant. La différence entre les deux formes de syntaxe provient de l'ordre dans lequel le préprocesseur recherche les fichiers de bibliothèque de type lorsque le chemin d'accès est spécifié de manière incomplète.

|Forme syntaxique|Action|
|-----------------|------------|
|Forme avec guillemets|Indique au préprocesseur de rechercher d’abord les fichiers de bibliothèque de types dans le répertoire du fichier qui contient l’instruction **#import** , puis dans les répertoires des fichiers qui incluent (`#include`) ce fichier. Le préprocesseur explore ensuite les chemins d’accès spécifiés ci-dessous.|
|Forme avec crochets pointus|Indique au préprocesseur de rechercher les fichiers bibliothèques de types en utilisant les chemins d’accès suivants :<br /><br /> 1.  Liste `PATH` des chemins d’accès de la variable d’environnement<br />2.  Liste `LIB` des chemins d’accès de la variable d’environnement<br />3.  Chemin d’accès spécifié par l’option du compilateur [/i](../build/reference/i-additional-include-directories.md) , à l’exception du fait que le compilateur recherche une bibliothèque de types qui a été référencée à partir d’une autre bibliothèque de types avec l’attribut [no_registry](../preprocessor/no-registry.md) .|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>Spécifier l’ID de localisation et le numéro de version

Lorsque vous spécifiez un progid, vous pouvez également spécifier l'ID de localisation et le numéro de version du progid. Par exemple :

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

Si vous ne spécifiez pas d’ID de localisation, un ProgID est choisi selon les règles suivantes :

- S’il n’existe qu’un seul ID de localisation, celui-ci est utilisé.

- S’il existe plusieurs ID de localisation, le premier avec le numéro de version 0, 9 ou 409 est utilisé.

- S’il existe plus d’un ID de localisation et qu’aucun d’entre eux n’est 0, 9 ou 409, le dernier est utilisé.

- Si vous ne spécifiez pas de numéro de version, la version la plus récente est utilisée.

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>Fichiers d’en-tête créés par l’importation

**#import** crée deux fichiers d’en-tête qui reconstruisent le C++ contenu de la bibliothèque de types dans le code source. Le fichier d’en-tête principal est similaire à celui produit par le compilateur Microsoft Interface Definition Language (MIDL), mais avec du code et des données supplémentaires générés par le compilateur. Le [fichier d’en-tête principal](#_predir_the_primary_type_library_header_file) a le même nom de base que la bibliothèque de types, plus un. Extension TLH. Le fichier d’en-tête secondaire possède le même nom de base que la bibliothèque de types, avec une extension .TLI. Il contient les implémentations des fonctions membres générées par le compilateur, et est inclus (`#include`) dans le fichier d'en-tête principal.

Si vous importez une propriété `byref` dispinterface qui utilise des paramètres, **#import** ne génère pas d’instruction [_ _ declspec (Property)](../cpp/property-cpp.md) pour la fonction.

Les deux fichiers d’en-tête sont placés dans le répertoire de sortie spécifié par l’option [/FO (nom du fichier objet)](../build/reference/fo-object-file-name.md) . Ils sont ensuite lus et compilés par le compilateur comme si le fichier d’en-tête principal `#include` était nommé par une directive.

Les optimisations de compilateur suivantes sont fournies avec la directive **#import** :

- Le fichier d'en-tête, une fois créé, porte le même horodatage que la bibliothèque de types.

- Lorsque **#import** est traité, le compilateur vérifie d’abord si l’en-tête existe et s’il est à jour. Si c’est le cas, il n’a pas besoin d’être recréé.

La directive **#import** participe également à une régénération minimale et peut être placée dans un fichier d’en-tête précompilé.  Pour plus d’informations, consultez [création de fichiers d’en-tête précompilés](../build/creating-precompiled-header-files.md).

### <a name="_predir_the_primary_type_library_header_file"></a>Fichier d’en-tête de la bibliothèque de types principale

Le fichier d'en-tête principal de bibliothèque de types se compose de sept sections :

- Titre réutilisable : Se compose de commentaires `#include` , d’instruction pour ComDef. H (qui définit des macros standard utilisées dans l’en-tête) et d’autres informations de configuration diverses.

- Références anticipées et typedefs : Se compose de déclarations de structure `struct IMyInterface` telles que et de typedefs.

- Déclarations de pointeur intelligent : La classe `_com_ptr_t` de modèle est un pointeur intelligent. Il encapsule les pointeurs d’interface et élimine la nécessité d' `AddRef`appeler `Release`les fonctions `QueryInterface` , et. Il masque également l’appel `CoCreateInstance` lors de la création d’un nouvel objet com. Cette section utilise l’instruction `_COM_SMARTPTR_TYPEDEF` macro pour établir des typedefs d’interfaces COM comme spécialisations de modèle de la classe de modèle [_com_ptr_t](../cpp/com-ptr-t-class.md) . Par exemple, pour l' `IMyInterface`interface, le. Le fichier TLH contiendra :

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   ce que le compilateur développe en :

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   Le type `IMyInterfacePtr` peut alors être utilisé à la place du pointeur d'interface brut `IMyInterface*`. Par conséquent, il n’est pas nécessaire d’appeler `IUnknown` les différentes fonctions membres

- Déclarations TypeInfo : Se compose principalement de définitions de classe et d’autres éléments qui exposent les `ITypeLib:GetTypeInfo`éléments TypeInfo individuels retournés par. Dans cette section, chaque typeinfo de la bibliothèque de types est répercuté dans l'en-tête en fonction des informations de `TYPEKIND`.

- Définition de GUID de style ancien facultatif : Contient les initialisations des constantes GUID nommées. Ces noms se présentent sous `CLSID_CoClass` la `IID_Interface`forme et, à l’instar de ceux générés par le compilateur MIDL.

- Instruction `#include` pour l'en-tête de bibliothèque de types secondaires.

- Réutilisable du pied de page : Contient `#pragma pack(pop)`actuellement.

Toutes les sections, à l’exception de la section de l’en-tête et du pied de page, sont placées `library` dans un espace de noms dont le nom est spécifié par l’instruction dans le fichier IDL d’origine. Vous pouvez utiliser les noms de l’en-tête de la bibliothèque de types par une qualification explicite à l’aide du nom de l’espace de noms. Vous pouvez également inclure l’instruction suivante :

```cpp
using namespace MyLib;
```

immédiatement après l’instruction **#import** dans le code source.

L’espace de noms peut être supprimé à l’aide de l’attribut [no_namespace](no-namespace.md)) de la directive **#import** . Toutefois, la suppression de l'espace de noms peut entraîner des collisions de noms. L’espace de noms peut également être renommé par l’attribut [rename_namespace](rename-namespace.md) .

Le compilateur fournit le chemin d’accès complet à toutes les dépendances de bibliothèque de types requises par la bibliothèque de types qu’il traite actuellement. Le chemin d’accès est écrit, sous forme de commentaires, dans l’en-tête de bibliothèque de types (.TLH) que le compilateur génère pour chaque bibliothèque de types traitée.

Si une bibliothèque de types inclut des références aux types définis dans d'autres bibliothèques de types, le fichier .TLH inclura des commentaires du type suivant :

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

Le nom de fichier réel dans le **#import** commentaire est le chemin d’accès complet de la bibliothèque de types à références croisées, tel qu’il est stocké dans le registre. Si vous rencontrez des erreurs provoquées par des définitions de type manquantes, vérifiez les commentaires au début du. TLH pour voir quelles bibliothèques de types dépendants devront peut-être être importées en premier. Les erreurs possibles sont des erreurs de syntaxe, par exemple C2143, C2146, C2321, C2501 (decl-specifiers absents) ou C2433 (« inline » non autorisé dans la déclaration de données) lors de la compilation du fichier .TLI.

Pour résoudre les erreurs de dépendance, déterminez les commentaires de dépendance qui ne sont pas fournis autrement pour les en-têtes système, puis fournissez une directive **#import** à un moment donné avant la directive **#import** de la bibliothèque de types dépendante.

### <a name="_predir_the_23import_directive_import_attributes"></a>attributs #import

**#import** pouvez éventuellement inclure un ou plusieurs attributs. Ces attributs demandent au compilateur de modifier le contenu des en-têtes de bibliothèque de types. Un symbole de **\\** barre oblique inverse () peut être utilisé pour inclure des lignes supplémentaires dans une seule instruction **#import** . Par exemple :

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

Pour plus d’informations, consultez [#import attributs](../preprocessor/hash-import-attributes-cpp.md).

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)\
[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)
