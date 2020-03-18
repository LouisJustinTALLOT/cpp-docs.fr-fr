---
title: '&lt;filesystem&gt;, fonctions'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: 1ab57a6fc13a03d02963f3d7ecc80f63decb9487
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421820"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt;, fonctions

Ces fonctions gratuites dans l’en-tête [\<filesystem >](../standard-library/filesystem.md) modifient et interrogent les opérations sur les chemins, les fichiers, les liens symboliques, les répertoires et les volumes. Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a>entièrement

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La fonction retourne le chemin d’accès absolu correspondant à *pval* par rapport au chemin d’accès `base`:

1. Si `pval.has_root_name() && pval.has_root_directory()` la fonction retourne *pval*.

1. Si `pval.has_root_name() && !pval.has_root_directory()` la fonction retourne `pval.root_name()` / `absolute(base).root_directory()` / `absolute(base).relative_path()` / .`pval.relative_path()`

1. Si `!pval.has_root_name() && pval.has_root_directory()` la fonction retourne `absolute(base).root_name()` / *pval*.

1. Si `!pval.has_root_name() && !pval.has_root_directory()` la fonction retourne `absolute(base)` / *pval*.

## <a name="begin"></a>commencer

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Les deux fonctions retournent *ITER*.

## <a name="canonical"></a>autorisés

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Les fonctions forment un chemin d’accès absolu `pabs = absolute(pval, base)` (ou `pabs = absolute(pval)` pour la surcharge sans paramètre de base), puis la réduisent à une forme canonique dans la séquence d’étapes suivante :

1. Chaque `X` de composant de chemin d’accès pour lequel `is_symlink(X)` a la **valeur true** est remplacé par `read_symlink(X)`.

1. Chaque `.` de composant de chemin d’accès (point est le répertoire actif établi par les composants du chemin précédent) est supprimé.

1. Chaque paire de composants de chemin d’accès `X`/`..` (point-point est le répertoire parent établi par les composants du chemin précédent) est supprimée.

La fonction retourne ensuite `pabs`.

## <a name="copy"></a>reprographie

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Toutes les fonctions sont susceptibles de copier ou de lier un ou plusieurs fichiers à *partir* de à *pour* sous le contrôle de *OPTS*, qui est considéré comme `copy_options::none` pour les surcharges sans paramètre *OPTS* . les *OPTS* doivent contenir au plus un des éléments suivants :

- `skip_existing`, `overwrite_existing` ou `update_existing`

- `copy_symlinks` ou `skip_symlinks`

- `directories_only`, `create_symlinks` ou `create_hard_links`

Les fonctions déterminent d’abord les valeurs de file_status `f` pour *from* et `t` pour *à*:

- Si `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, en appelant `symlink_status`

- Sinon, en appelant `status`

- Sinon, elles signalent une erreur.

Si `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, elles signalent une erreur (et ne font rien d’autre).

Sinon, si `is_symlink(f)` Then :

- Si `options & copy_options::skip_symlinks`, ne faites rien.

- Sinon, si `!exists(t)&& options & copy_options::copy_symlinks`, `copy_symlink(from, to, opts)`.

- Dans le cas contraire, signalez une erreur.

Sinon, si `is_regular_file(f)`, alors :

- Si `opts & copy_options::directories_only`, ne faites rien.

- Sinon, si `opts & copy_options::create_symlinks`, `create_symlink(to, from)`.

- Sinon, si `opts & copy_options::create_hard_links`, `create_hard_link(to, from)`.

- Sinon, si `is_directory(f)`, `copy_file(from, to` / `from.filename(), opts)`.

- Sinon, valeur `copy_file(from, to, opts)`.

Sinon, si `is_directory(f) && (opts & copy_options::recursive || !opts)`, alors :

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

Sinon, ne rien faire.

## <a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Toutes les fonctions copient éventuellement le fichier à partir *de vers sous le* contrôle de *OPTS*, qui est considéré comme `copy_options::none` pour les surcharges sans paramètre *OPTS* . les *OPTS* doivent contenir au plus un des `skip_existing`, `overwrite_existing`ou `update_existing`.

Si `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, signaler comme une erreur indiquant que le fichier existe déjà.

Sinon, si `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`, tentez de copier le contenu et les attributs *du fichier de vers le fichier.* Signaler comme erreur si la tentative de copie échoue.

Les fonctions retournent **true** si la copie est tentée et réussie ; sinon, **false**.

## <a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si `is_directory(from)`, la fonction appelle `create_directory_symlink(from, to)`. Sinon, elle appelle `create_symlink(from, to)`.

## <a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pour un nom de chemin d’accès tel qu’un\/b\/c, la fonction crée les répertoires a et a\/b en fonction des besoins afin de pouvoir créer le répertoire a\/b\/c en fonction des besoins. Elle retourne **true** uniquement si elle crée réellement le répertoire *pval*.

## <a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La fonction crée le répertoire *pval* si nécessaire. Elle retourne true uniquement si elle crée réellement le répertoire *pval*, auquel cas elle copie les autorisations à partir du fichier existant *attr*, ou utilise `perms::all` pour les surcharges sans paramètre *attr* .

## <a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien comme lien *symbolique vers le répertoire.*

## <a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien sous forme de lien physique vers le répertoire ou *le fichier.*

## <a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien en tant que *lien* symbolique *vers le fichier.*

## <a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Les fonctions sans paramètre *pval* retournent le chemin d’accès du répertoire actif. Les fonctions restantes définissent le répertoire actuel sur *pval*.

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La première fonction retourne `directory_iterator()` et la deuxième fonction retourne `recursive_directory_iterator()`

## <a name="equivalent"></a>identique

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Les fonctions retournent **true** uniquement si *Left* et *Right* choisissent la même entité FileSystem.

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `status_known && stat.type() != file_not_found`. Les deuxième et troisième fonctions retournent `exists(status(pval))`.

## <a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent la taille en octets du fichier choisi par *pval*, si `exists(pval) && is_regular_file(pval)` et que la taille du fichier peut être déterminée. Dans le cas contraire, elles signalent une erreur et retournent `uintmax_t(-1)`.

## <a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La fonction retourne le nombre de liens physiques pour *pval*, ou \-1 si une erreur se produit.

## <a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La fonction retourne une valeur de hachage pour `pval.native()`.

## <a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::block`. Les fonctions restantes retournent `is_block_file(status(pval))`.

## <a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::character`. Les fonctions restantes retournent `is_character_file(status(pval))`.

## <a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::directory`. Les fonctions restantes retournent `is_directory_file(status(pval))`.

## <a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si `is_directory(pval)`, la fonction retourne `directory_iterator(pval) == directory_iterator()`; Sinon, elle retourne `file_size(pval) == 0`.

## <a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::fifo`. Les fonctions restantes retournent `is_fifo(status(pval))`.

## <a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::other`. Les fonctions restantes retournent `is_other(status(pval))`.

## <a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::regular`. Les fonctions restantes retournent `is_regular_file(status(pval))`.

## <a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::socket`. Les fonctions restantes retournent `is_socket(status(pval))`.

## <a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::symlink`. Les fonctions restantes retournent `is_symlink(status(pval))`.

## <a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Les deux premières fonctions retournent l’heure de la dernière modification des données pour *pval*, ou `file_time_type(-1)` si une erreur se produit. Les deux dernières fonctions définissent l’heure de la dernière modification des données de *pval* à *NEW_TIME*.

## <a name="permissions"></a>autorisations

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Les fonctions définissent les autorisations pour le chemin d’accès choisi par *pval* pour `mask & perms::mask` sous le contrôle de `perms & (perms::add_perms | perms::remove_perms)`. *Mask* doit contenir au plus une des `perms::add_perms` et `perms::remove_perms`.

Si `mask & perms::add_perms`, les fonctions définissent les autorisations sur `status(pval).permissions() | mask & perms::mask`. Sinon, si `mask & perms::remove_perms`, les fonctions définissent les autorisations sur `status(pval).permissions() & ~(mask & perms::mask)`. Dans le cas contraire, les fonctions définissent les autorisations sur `mask & perms::mask`.

## <a name="proximate"></a>approximative

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Les fonctions signalent une erreur et retournent `path()` si `!is_symlink(pval)`. Sinon, les fonctions retournent un objet de type `path` contenant le lien symbolique.

## <a name="relative"></a>parent

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a>Installez

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent **true** uniquement si `exists(symlink_status(pval))` et si le fichier est supprimé avec succès. Un lien symbolique est lui-même supprimé, pas le fichier qu’il choisit.

## <a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si *pval* est un répertoire, les fonctions suppriment de manière récursive toutes les entrées de répertoire, puis l’entrée elle-même. Sinon, les fonctions appellent `remove`. Elles retournent un comptage de tous les éléments qui ont été supprimés.

## <a name="rename"></a>renommer

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Les fonctions renomment *de* *en.* Un lien symbolique est lui-même renommé, pas le fichier qu’il choisit.

## <a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Les fonctions altèrent la taille d’un fichier de telle sorte que `file_size(pval) == size`

## <a name="space"></a>espace

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La fonction retourne des informations sur le volume choisi par *pval*, dans une structure de type `space_info`. La structure contient `uintmax_t(-1)` pour toute valeur qui ne peut pas être déterminée.

## <a name="status"></a>statu

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent l’état du chemin d’accès, le type de fichier et les autorisations associés à *pval*. Un lien symbolique n’est lui-même pas testé, mais le fichier qu’il choisit.

## <a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La fonction retourne `stat.type() != file_type::none`

## <a name="swap"></a>échange

```cpp
void swap(path& left, path& right) noexcept;
```

La fonction échange le contenu de *gauche* et de *droite*.

## <a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Les fonctions retournent l’état du lien symbolique du chemin d’accès, le type de fichier et les autorisations associés à *pval*. Les fonctions se comportent de la même façon que `status(pval)`, sauf qu’un lien symbolique est lui-même testé, et non le fichier qu’il choisit.

## <a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Les fonctions retournent un nom de chemin absolu qui prend en compte si nécessaire le répertoire actuel associé au nom de sa racine. \(pour POSIX, les fonctions retournent `absolute(pval)`.\)

## <a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Les fonctions retournent un nom de chemin pour un répertoire approprié à des fichiers conteneurs temporaires.

## <a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

La première fonction se comporte comme `path(source)` et la deuxième fonction se comporte comme `path(first, last)`, sauf que la source choisie dans chaque cas est prise comme une séquence d’éléments char encodés au format UTF-8, quel que soit le système de fichiers.

## <a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
