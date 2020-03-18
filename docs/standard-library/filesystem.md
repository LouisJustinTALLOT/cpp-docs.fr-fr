---
title: '&lt;filesystem&gt;'
description: Décrit les classes, les fonctions et les types dans l’en-tête filesystem C++ de la bibliothèque standard.
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: f9e384953a4e675ad6235a274c447031976a1585
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441710"
---
# &lt;filesystem&gt;

Incluez l’en-tête &lt;filesystem> pour accéder aux classes et aux fonctions qui manipulent et récupèrent des informations sur les chemins, les fichiers et les répertoires.

## <a name="syntax"></a>Syntaxe

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> À la sortie de Visual Studio 2017, l’en-tête > filesystem\<n’était C++ pas encore une norme. C++dans Visual Studio 2017 RTW implémente la norme préliminaire finale, qui se trouve dans [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf). Visual Studio 2017 version 15,7 et versions ultérieures prennent en charge la nouvelle version C++ 17 \<filesystem> standard.
> Il s’agit d’une implémentation entièrement nouvelle, incompatible avec la version précédente de `std::experimental`. Il a été rendu nécessaire par la prise en charge des liens symboliques, les correctifs de bogues et les modifications du comportement requis standard. À l’heure actuelle, y compris \<filesystem> fournit le nouvel `std::filesystem` et le `std::experimental::filesystem`précédent. Notamment \<experimental/filesystem> fournit uniquement l’ancienne implémentation de experimental. L’implémentation de experimental sera supprimée dans la prochaine version suivante des bibliothèques.

Cet en-tête prend en charge les systèmes de fichiers pour l’une des deux grandes classes de systèmes d’exploitation hôtes : Microsoft Windows et POSIX.

Bien que la plupart des fonctionnalités soit communes aux deux systèmes d’exploitation, ce document met l’accent sur les différences. Par exemple :

- Windows prend en charge plusieurs noms racines, tels que `c:` ou `\\network_name`. Un système de fichiers se compose d’une forêt d’arborescences, chacune ayant son propre répertoire racine, par exemple `c:\` ou `\\network_name\`, et chacune avec son propre répertoire actif, pour la réalisation d’un chemin d’accès relatif (un nom de chemin d’accès absolu).

- POSIX prend en charge une arborescence unique, sans nom racine, le répertoire racine unique `/`et un répertoire actif unique.

Une autre différence importante réside dans la représentation native des chemins :

- Windows utilise une séquence de **wchar_t** se terminant par un caractère null, encodée au format UTF-16 (un ou plusieurs éléments pour chaque caractère).

- POSIX utilise une séquence de **char** se terminant par un caractère null, encodée au format UTF-8 (un ou plusieurs éléments pour chaque caractère).

- Un objet de la classe `path` stocke le chemin d’accès au format natif, mais prend en charge une conversion facile entre ce formulaire stocké et plusieurs formulaires externes :

  - Séquence de **char** se terminant par un caractère null, encodée comme privilégié par le système d’exploitation.

  - Séquence de **char** se terminant par un caractère null, encodée au format UTF-8.

  - Séquence de **wchar_t** se terminant par un caractère null, encodée comme privilégié par le système d’exploitation.

  - Séquence de **char16_t** se terminant par un caractère null, encodée au format UTF-16.

  - Séquence de **char32_t** se terminant par un caractère null, encodée au format UTF-32.

  Selon les besoins, les conversions entre ces représentations passent par une ou plusieurs facettes `codecvt`. Si aucun objet de paramètres régionaux spécifique n’est spécifié, ces facettes sont obtenues à partir des paramètres régionaux globaux.

Il existe une autre différence, la précision avec laquelle chaque système d’exploitation vous permet de spécifier les autorisations d’accès aux fichiers ou répertoires :

- Windows enregistre si un fichier est en lecture seule ou en écriture, un attribut qui n’a aucune signification pour les répertoires.

- POSIX enregistre si un fichier peut être lu, écrit ou exécuté (analysé, s’il s’agit d’un répertoire). Et, si chaque opération est autorisée pour le propriétaire, le groupe du propriétaire ou pour tout le monde, ainsi que quelques autres autorisations.

Pour les deux systèmes, la structure imposée au chemin après le nom de la racine est la même. Pour le chemin d’accès `c:/abc/xyz/def.ext`:

- Le nom de la racine est `c:`.

- Le répertoire racine est `/`.

- Le chemin d’accès racine est `c:/`.

- Le chemin d’accès relatif est `abc/xyz/def.ext`.

- Le chemin d’accès parent est `c:/abc/xyz`.

- Le nom de fichier est `def.ext`.

- Le radical est `def`.

- L’extension est `.ext`.

Une différence mineure est le séparateur par défaut entre la séquence de répertoires dans un chemin d’accès. Les deux systèmes d’exploitation vous permettent d’écrire une barre oblique `/`, mais dans certains contextes, Windows préfère une barre oblique inverse `\`. L’implémentation stocke son séparateur préféré dans le membre de données `preferred_separator` dans `path`.

Enfin, `path` objets ont une fonctionnalité importante : vous pouvez les utiliser partout où un argument de nom de fichier est requis dans les classes définies dans l’en-tête [\<fstream >](fstream.md).

Pour plus d’informations et d’exemples de code, consultez [navigationC++dans le système de fichiers ()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[classe directory_entry](../standard-library/directory-entry-class.md)|Décrit un objet retourné par un `directory_iterator` ou un `recursive_directory_iterator` et qui contient un `path`.|
|[classe directory_iterator](../standard-library/directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers.|
|[classe filesystem_error](../standard-library/filesystem-error-class.md)|Classe de base pour les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.|
|[Path, classe](../standard-library/path-class.md)|Définit une classe qui stocke un objet de type de modèle `String` qui peut être utilisé comme nom de fichier.|
|[classe recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers. L'itérateur peut également descendre dans des sous-répertoires.|
|[classe file_status](../standard-library/file-status-class.md)|Encapsule un `file_type`.|

### <a name="structs"></a>Structs

|||
|-|-|
|[structure space_info](../standard-library/space-info-structure.md)|Contient des informations sur un volume.|

## <a name="functions"></a>Fonctions

[\<filesystemfonctions >](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Opérateurs

[\<filesystemopérateurs >](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Énumérations

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/filesystem-functions.md#copy_file) et qui détermine le comportement si un fichier de destination existe déjà.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Énumération qui spécifie les options pour les itérateurs de répertoire.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Énumération pour les types de fichiers.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| Énumère les options de la fonction `permissions`. |
|[perms](../standard-library/filesystem-enumerations.md#perms)|Type de masque de bits utilisé pour transmettre les autorisations et les options des autorisations|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
