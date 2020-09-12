---
title: '&lt;filesystem&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: 3c94ec899f0ea7abf71530f6aca44638fdb216c9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041937"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt;, énumérations

Cette rubrique décrit les énumérations de l’en-tête filesystem.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<experimental/filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="copy_options"></a><a name="copy_options"></a> copy_options

Énumération de valeurs de masque de bits utilisée avec les fonctions [copy](filesystem-functions.md#copy) et [copy_file](filesystem-functions.md#copy_file) pour spécifier le comportement.

### <a name="syntax"></a>Syntaxe

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>Valeurs

| Nom | Description |
|------------|-----------------|
|`none`|Exécute le comportement par défaut de l’opération.|
|`skip_existing`|Ne pas copier si le fichier existe déjà, ne pas signaler une erreur.|
|`overwrite_existing`|Remplacer le fichier s'il existe déjà.|
|`update_existing`|Remplacer le fichier s’il existe déjà et qu’il est plus ancien que le remplacement.|
|`recursive`|Copier dans les sous-répertoires et leur contenu de façon récursive.|
|`copy_symlinks`|Copier les liens symboliques sous la forme de liens symboliques, au lieu de copier les fichiers vers lesquels ils pointent.|
|`skip_symlinks`|Ignorer les liens symboliques.|
|`directories_only`|Itérer uniquement sur les répertoires, ignorer les fichiers.|
|`create_symlinks`|Créer des liens symboliques au lieu de copier les fichiers. Un chemin absolu doit servir de chemin source, sauf si la destination est le répertoire actuel.|
|`create_hard_links`|Créer des liens physiques au lieu de copier les fichiers.|

## <a name="directory_options"></a><a name="directory_options"></a> directory_options

Spécifie s'il faut suivre les liens symboliques vers des répertoires ou les ignorer.

### <a name="syntax"></a>Syntaxe

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`none`|Comportement par défaut : ignorer les liens symboliques vers les répertoires. Autorisation refusée est une erreur.|
|`follow_directory_symlink`|Traiter les liens symboliques vers des répertoires comme des répertoires réels.|

## <a name="file_type"></a><a name="file_type"></a> file_type

Énumération pour les types de fichiers. Les valeurs prises en charge sont Regular, Directory, not_found et Unknown.

### <a name="syntax"></a>Syntaxe

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>Valeurs

|Nom|Valeur|Description|
|----------|-----------|-----------------|
|`not_found`|-1|Représente un fichier qui n'existe pas.|
|`none`|0|Représente un fichier qui n'a aucun attribut de type. (Non pris en charge.)|
|`regular`|1|Représente un fichier de disque conventionnel.|
|`directory`|2|Représente un répertoire.|
|`symlink`|3|Représente un lien symbolique. (Non pris en charge.)|
|`block`|4|Représente un fichier spécial de bloc sur les systèmes UNIX. (Non pris en charge.)|
|`character`|5|Représente un fichier spécial de caractères sur les systèmes UNIX. (Non pris en charge.)|
|`fifo`|6|Représente un fichier FIFO sur les systèmes UNIX. (Non pris en charge.)|
|`socket`|7|Représente un socket sur les systèmes UNIX. (Non pris en charge.)|
|`unknown`|8|Représente un fichier dont l'état ne peut pas être déterminé.|

## <a name="perm_options"></a><a name="perm_options"></a> perm_options

Comprend `replace` les valeurs,, `add` `remove` et `nofollow` .

```cpp
enum class perm_options;
```

## <a name="perms"></a><a name="perms"></a> perms

Indicateurs pour les autorisations de fichiers. Les valeurs prises en charge sont essentiellement « ReadOnly » et All. Pour un fichier en lecture seule, aucun des bits *_write n'est défini. Sinon, le bit `all` (0x0777) est défini.

### <a name="syntax"></a>Syntaxe

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
