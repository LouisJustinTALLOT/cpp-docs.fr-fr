---
title: '&lt;filesystem&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: 0f2c90bd7c1d88a94d1dab05b98442111faa71a2
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898813"
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

Incluez l’en-tête &lt;filesystem> pour accéder aux classes et aux fonctions qui manipulent et récupèrent des informations sur les chemins, les fichiers et les répertoires.

## <a name="syntax"></a>Syntaxe

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Depuis la sortie de Visual Studio 2017, l’en-tête \<FileSystem > n’était pas C++ encore une norme. C++dans Visual Studio 2017 (MSVC V141) implémente la norme préliminaire finale, trouvée dans [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Cet en-tête prend en charge les systèmes de fichiers pour l’une des deux grandes classes de systèmes d’exploitation hôtes : Microsoft Windows et POSIX.

Bien que la plupart des fonctionnalités soit communes aux deux systèmes d’exploitation, ce document met l’accent sur les différences. Par exemple :

- Windows prend en charge plusieurs noms de racines, par exemple, c: ou \\\nom_réseau. Un système de fichiers se compose d’une forêt d’arborescences, chacune ayant son propre répertoire racine, par exemple, c:\ ou \\\nom_réseau\\, et chacune ayant son propre répertoire actif pour compléter un chemin relatif (le contraire d’un chemin absolu).

- POSIX prend en charge une arborescence unique, sans nom racine, le répertoire racine unique/et un répertoire actif unique.

Une autre différence importante réside dans la représentation native des chemins :

- Windows utilise une séquence wchar_t terminée par un caractère null, codée au format UTF-16 (un ou deux éléments pour chaque caractère).

- POSIX utilise une séquence de caractères se terminant par un caractère null, encodée au format UTF-8 (un ou plusieurs éléments pour chaque caractère).

- Un objet de classe path stocke le chemin au format natif. Toutefois, il prend en charge la conversion (avec simplicité) entre ce format stocké et plusieurs formats externes :

- Séquence char terminée par un caractère null, codée au format préconisé par le système d’exploitation.

- Séquence char terminée par un caractère null, codée au format UTF-8.

- Séquence wchar_t terminée par un caractère null, codée au format préconisé par le système d’exploitation.

- Séquence char16_t terminée par un caractère null, codée au format UTF-16.

- Séquence char32_t terminée par un caractère null, codée au format UTF-32.

Selon les besoins, les conversions entre ces représentations passent par une ou plusieurs facettes `codecvt`. Si aucun objet de paramètres régionaux spécifique n’est désigné, ces facettes sont obtenues à partir des paramètres régionaux globaux.

Il existe une autre différence, la précision avec laquelle chaque système d’exploitation vous permet de spécifier les autorisations d’accès aux fichiers ou répertoires :

1. Windows enregistre si un fichier est accessible en lecture seule ou en écriture, un attribut qui n’a aucune signification pour les répertoires.

1. POSIX enregistre si un fichier peut être lu, écrit ou exécuté (analysé dans le cas d’un répertoire), par le propriétaire, par le groupe du propriétaire ou par tout le monde, ainsi que par d’autres autorisations.

Pour les deux systèmes, la structure imposée au chemin après le nom de la racine est la même. Pour le chemin c:/abc/xyz/def.ext :

- Le nom de la racine est c:.

- Le répertoire racine est /.

- Le chemin racine est c: /.

- Le chemin relatif est abc/xyz/def.ext.

- Le chemin parent est c:/abc/xyz.

- Le nom de fichier est def.ext.

- La racine est def.

- L’extension est .ext.

Il existe une petite différence au niveau du **séparateur par défaut**dans la séquence de répertoires d’un chemin. Les deux systèmes d’exploitation vous permettent d’écrire une barre oblique /, toutefois, dans certains contextes, Windows préfère une barre oblique inverse \\.

Enfin, les objets path ont une fonctionnalité importante : vous pouvez les utiliser partout où un argument de nom de fichier est nécessaire dans les classes définies dans l’en-tête \<fstream>.

Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[directory_entry, classe](../standard-library/directory-entry-class.md)|Décrit un objet retourné par un `directory_iterator` ou un `recursive_directory_iterator` et contient un chemin.|
|[directory_iterator, classe](../standard-library/directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers.|
|[filesystem_error, classe](../standard-library/filesystem-error-class.md)|Classe de base pour les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.|
|[path, classe](../standard-library/path-class.md)|Définit une classe qui stocke un objet de type de modèle `String` qui peut être utilisé comme nom de fichier.|
|[recursive_directory_iterator, classe](../standard-library/recursive-directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers. L'itérateur peut également descendre dans des sous-répertoires.|
|[file_status, classe](../standard-library/file-status-class.md)|Encapsule un `file_type`.|

### <a name="structs"></a>Structures

|||
|-|-|
|[space_info, structure](../standard-library/space-info-structure.md)|Contient des informations sur un volume.|

## <a name="functions"></a>Fonctions

[\<filesystem>, fonctions](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Opérateurs

[\<filesystem>, opérateurs](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Énumérations

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/filesystem-functions.md#copy_file) qui détermine le comportement si un fichier de destination existe déjà.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/filesystem-functions.md#copy_file) qui détermine le comportement si un fichier de destination existe déjà.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Énumération qui spécifie les options pour les itérateurs de répertoire.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Énumération pour les types de fichiers.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[perms](../standard-library/filesystem-enumerations.md#perms)|Type de masque de bits utilisé pour transmettre les autorisations et les options des autorisations|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
