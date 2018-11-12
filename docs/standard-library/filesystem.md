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
ms.openlocfilehash: 54817eeeba0b885cbf3de558c04fe2eb5d6e14fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473383"
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
> Depuis la version finale de Visual Studio 2017, le \<filesystem > en-tête n’était pas encore une norme C++. Visual C++ 2017 implémente le projet final de la norme, qui se trouve dans [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Cet en-tête prend en charge les systèmes de fichiers des deux grandes classes de systèmes d’exploitation : Microsoft Windows et Posix.

Bien que la plupart des fonctionnalités soit communes aux deux systèmes d’exploitation, ce document met l’accent sur les différences. Exemple :

- Windows prend en charge plusieurs noms de racines, par exemple, c: ou \\\nom_réseau. Un système de fichiers se compose d’une forêt d’arborescences, chacune ayant son propre répertoire racine, par exemple, c:\ ou \\\nom_réseau\\, et chacune ayant son propre répertoire actif pour compléter un chemin relatif (le contraire d’un chemin absolu).

- Posix prend en charge une arborescence unique (sans nom de la racine), le répertoire racine unique / et un répertoire actif unique.

Une autre différence importante réside dans la représentation native des chemins :

- Windows utilise une séquence wchar_t terminée par un caractère null, codée au format UTF-16 (un ou deux éléments pour chaque caractère).

- Posix utilise une séquence char terminée par un caractère null, codée au format UTF-8 (un ou plusieurs éléments pour chaque caractère).

- Un objet de classe path stocke le chemin au format natif. Toutefois, il prend en charge la conversion (avec simplicité) entre ce format stocké et plusieurs formats externes :

- Séquence char terminée par un caractère null, codée au format préconisé par le système d’exploitation.

- Séquence char terminée par un caractère null, codée au format UTF-8.

- Séquence wchar_t terminée par un caractère null, codée au format préconisé par le système d’exploitation.

- Séquence char16_t terminée par un caractère null, codée au format UTF-16.

- Séquence char32_t terminée par un caractère null, codée au format UTF-32.

Selon les besoins, les conversions entre ces représentations passent par une ou plusieurs facettes `codecvt`. Si aucun objet de paramètres régionaux spécifique n’est désigné, ces facettes sont obtenues à partir des paramètres régionaux globaux.

Il existe une autre différence, la précision avec laquelle chaque système d’exploitation vous permet de spécifier les autorisations d’accès aux fichiers ou répertoires :

1. Windows enregistre si un fichier est accessible en lecture seule ou en écriture, un attribut qui n’a aucune signification pour les répertoires.

1. Posix enregistre si un fichier peut être lu, écrit ou exécuté (analysé, s’il s’agit d’un répertoire) par son propriétaire, par le groupe de son propriétaire ou par tout le monde. En outre, il enregistre quelques autorisations supplémentaires.

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

## <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[directory_entry, classe](../standard-library/directory-entry-class.md)|Décrit un objet retourné par un `directory_iterator` ou un `recursive_directory_iterator` et contient un chemin.|
|[directory_iterator, classe](../standard-library/directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers.|
|[filesystem_error, classe](../standard-library/filesystem-error-class.md)|Classe de base pour les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.|
|[path, classe](../standard-library/path-class.md)|Définit une classe qui stocke un objet de type de modèle `String` qui peut être utilisé comme nom de fichier.|
|[recursive_directory_iterator, classe](../standard-library/recursive-directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers. L'itérateur peut également descendre dans des sous-répertoires.|
|[file_status, classe](../standard-library/file-status-class.md)|Encapsule un `file_type`.|

## <a name="structs"></a>Structs

|Name|Description|
|----------|-----------------|
|[space_info, structure](../standard-library/space-info-structure.md)|Contient des informations sur un volume.|

## <a name="functions"></a>Fonctions

[\<filesystem>, fonctions](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Opérateurs

[\<filesystem>, opérateurs](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Énumérations

|Name|Description|
|----------|-----------------|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/filesystem-functions.md#copy_file) et qui détermine le comportement si un fichier de destination existe déjà.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/filesystem-functions.md#copy_file) et qui détermine le comportement si un fichier de destination existe déjà.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Énumération qui spécifie les options pour les itérateurs de répertoire.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Énumération pour les types de fichiers.|
|[Perms](../standard-library/filesystem-enumerations.md#perms)|Type de masque de bits utilisé pour transmettre les autorisations et les options des autorisations|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
