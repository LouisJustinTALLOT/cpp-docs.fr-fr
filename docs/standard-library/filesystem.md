---
title: '&lt;:::no-loc(filesystem):::&gt;'
description: "Décrit les classes, les fonctions et les types dans l' :::no-loc(filesystem)::: en-tête de la bibliothèque C++ standard."
ms.date: 01/22/2020
f1_keywords:
- <:::no-loc(filesystem):::>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- ':::no-loc(filesystem):::'
- ':::no-loc(experimental):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(char16_t):::'
- ':::no-loc(char32_t):::'
ms.openlocfilehash: 1b3f541619bde85131915a4d1586a44675c2906a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219142"
---
# &lt;:::no-loc(filesystem):::&gt;

Incluez l’en-tête &lt; :::no-loc(filesystem):::> pour accéder aux classes et aux fonctions qui manipulent et récupèrent des informations sur les chemins d’accès, les fichiers et les répertoires.

## <a name="syntax"></a>Syntaxe

```cpp
#include <:::no-loc(filesystem):::> // C++17 standard header file name
#include <:::no-loc(experimental):::/:::no-loc(filesystem):::> // Header file for pre-standard implementation
using namespace std:::::no-loc(experimental)::::::::no-loc(filesystem):::::v1;
```

> [!IMPORTANT]
> À la sortie de Visual Studio 2017, l' \<:::no-loc(filesystem):::> en-tête n’était pas encore une norme C++. C++ dans Visual Studio 2017 RTW implémente la norme préliminaire finale, trouvée dans la norme [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100). Visual Studio 2017 version 15,7 et versions ultérieures prennent en charge la nouvelle norme C++ 17 \<:::no-loc(filesystem):::> .
> Il s’agit d’une implémentation entièrement nouvelle, incompatible avec la `std:::::no-loc(experimental):::` version précédente. Il a été rendu nécessaire par la prise en charge des liens symboliques, les correctifs de bogues et les modifications du comportement requis standard. Actuellement, y compris \<:::no-loc(filesystem):::> fournit le nouveau `std:::::no-loc(filesystem):::` et le précédent `std:::::no-loc(experimental)::::::::no-loc(filesystem):::` . Y compris \<:::no-loc(experimental):::/:::no-loc(filesystem):::> fournit uniquement l’ancienne :::no-loc(experimental)::: implémentation. L' :::no-loc(experimental)::: implémentation sera supprimée dans la prochaine version suivante des bibliothèques.

Cet en-tête prend en charge les systèmes de fichiers pour l’une des deux grandes classes de systèmes d’exploitation hôtes : Microsoft Windows et POSIX.

Bien que la plupart des fonctionnalités soit communes aux deux systèmes d’exploitation, ce document met l’accent sur les différences. Par exemple :

- Windows prend en charge plusieurs noms racines, tels que `c:` ou `\\network_name` . Un système de fichiers se compose d’une forêt d’arborescences, chacune ayant son propre répertoire racine, tel que `c:\` ou `\\network_name\` , et chacun avec son propre répertoire actif, pour la réalisation d’un chemin d’accès relatif (un nom de chemin d’accès absolu).

- POSIX prend en charge une arborescence unique, sans nom racine, le répertoire racine unique `/` et un répertoire actif unique.

Une autre différence importante réside dans la représentation native des chemins :

- Windows utilise une séquence de type terminé par le caractère null **`:::no-loc(wchar_t):::`** , encodée au format UTF-16 (un ou plusieurs éléments pour chaque :::no-loc(char)::: acter).

- POSIX utilise une séquence de type terminé par le caractère null **`:::no-loc(char):::`** , encodée au format UTF-8 (un ou plusieurs éléments pour chaque :::no-loc(char)::: acter).

- Un objet de classe `path` stocke le nom de chemin d’accès au format natif, mais prend en charge une conversion facile entre ce formulaire stocké et plusieurs formulaires externes :

  - Séquence terminée par un caractère null **`:::no-loc(char):::`** , encodée comme privilégié par le système d’exploitation.

  - Séquence terminée par un caractère null **`:::no-loc(char):::`** , encodée au format UTF-8.

  - Séquence terminée par un caractère null **`:::no-loc(wchar_t):::`** , encodée comme privilégié par le système d’exploitation.

  - Séquence terminée par un caractère null **`:::no-loc(char16_t):::`** , encodée au format UTF-16.

  - Séquence terminée par un caractère null **`:::no-loc(char32_t):::`** , encodée au format UTF-32.

  Selon les besoins, les conversions entre ces représentations passent par une ou plusieurs facettes `codecvt`. Si aucun objet de paramètres régionaux spécifique n’est spécifié, ces facettes sont obtenues à partir des paramètres régionaux globaux.

Il existe une autre différence, la précision avec laquelle chaque système d’exploitation vous permet de spécifier les autorisations d’accès aux fichiers ou répertoires :

- Windows enregistre si un fichier est en lecture seule ou en écriture, un attribut qui n’a aucune signification pour les répertoires.

- POSIX enregistre si un fichier peut être lu, écrit ou exécuté (analysé, s’il s’agit d’un répertoire). Et, si chaque opération est autorisée pour le propriétaire, le groupe du propriétaire ou pour tout le monde, ainsi que quelques autres autorisations.

Pour les deux systèmes, la structure imposée au chemin après le nom de la racine est la même. Pour le chemin d’accès `c:/abc/xyz/def.ext` :

- Le nom de la racine est `c:` .

- Le répertoire racine est `/` .

- Le chemin d’accès racine est `c:/` .

- Le chemin d’accès relatif est `abc/xyz/def.ext` .

- Le chemin d’accès parent est `c:/abc/xyz` .

- Le nom de fichier est `def.ext`.

- Le radical est `def` .

- L’extension est `.ext` .

Une différence mineure est le séparateur par défaut entre la séquence de répertoires dans un chemin d’accès. Les deux systèmes d’exploitation vous permettent d’écrire une barre oblique `/` , mais dans certains contextes, Windows préfère une barre oblique inverse `\` . L’implémentation stocke son séparateur préféré dans le membre `preferred_separator` de données de `path` .

Enfin, les `path` objets ont une fonctionnalité importante : vous pouvez les utiliser partout où un argument de nom de fichier est requis dans les classes définies dans l’en-tête [\<fstream>](fstream.md) .

Pour plus d’informations et d’exemples de code, consultez navigation dans le [système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[directory_entry, classe](../standard-library/directory-entry-class.md)|Décrit un objet retourné par un `directory_iterator` ou un `recursive_directory_iterator` et contient un `path` .|
|[directory_iterator, classe](../standard-library/directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers.|
|[:::no-loc(filesystem):::classe _error](../standard-library/:::no-loc(filesystem):::-error-class.md)|Classe de base pour les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.|
|[path, classe](../standard-library/path-class.md)|Définit une classe qui stocke un objet de type de modèle `String` qui peut être utilisé comme nom de fichier.|
|[recursive_directory_iterator, classe](../standard-library/recursive-directory-iterator-class.md)|Décrit un itérateur d'entrée qui parcourt les noms de fichiers dans un répertoire de système de fichiers. L'itérateur peut également descendre dans des sous-répertoires.|
|[file_status, classe](../standard-library/file-status-class.md)|Encapsule un `file_type`.|

### <a name="structs"></a>Structures

|||
|-|-|
|[structure space_info](../standard-library/space-info-structure.md)|Contient des informations sur un volume.|

## <a name="functions"></a>Fonctions

[\<:::no-loc(filesystem):::>Mission](../standard-library/:::no-loc(filesystem):::-functions.md)

## <a name="operators"></a>Opérateurs

[\<:::no-loc(filesystem):::>Operator](../standard-library/:::no-loc(filesystem):::-operators.md)

## <a name="enumerations"></a>Énumérations

|||
|-|-|
|[copy_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#copy_options)|Énumération utilisée avec [copy_file](../standard-library/:::no-loc(filesystem):::-functions.md#copy_file) et qui détermine le comportement si un fichier de destination existe déjà.|
|[directory_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#directory_options)|Énumération qui spécifie les options pour les itérateurs de répertoire.|
|[file_type](../standard-library/:::no-loc(filesystem):::-enumerations.md#file_type)|Énumération pour les types de fichiers.|
|[perm_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#perm_options)| Énumère les options de la `permissions` fonction. |
|[perms](../standard-library/:::no-loc(filesystem):::-enumerations.md#perms)|Type de masque de bits utilisé pour transmettre les autorisations et les options des autorisations|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
