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
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332050"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt;, fonctions

Ces fonctions libres [ \<](../standard-library/filesystem.md) dans le système de fichiers>en-tête modifient et interrogent les opérations sur les chemins, les fichiers, les symlinks, les répertoires et les volumes. Pour obtenir plus d’informations et des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>Absolue

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La fonction renvoie le nom de chemin absolu correspondant `base`au *pval* par rapport au nom du chemin :

1. Si `pval.has_root_name() && pval.has_root_directory()` la fonction retourne *pval*.

1. Si `pval.has_root_name() && !pval.has_root_directory()` la `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`fonction revient .

1. Si `!pval.has_root_name() && pval.has_root_directory()` la `absolute(base).root_name()`  / fonction retourne *pval*.

1. Si `!pval.has_root_name() && !pval.has_root_directory()` la `absolute(base)`  / fonction retourne *pval*.

## <a name="begin"></a><a name="begin"></a>Commencer

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Les deux fonctions *retournent iter*.

## <a name="canonical"></a><a name="canonical"></a>Canonique

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Les fonctions forment toutes `pabs = absolute(pval, base)` un `pabs = absolute(pval)` nom de chemin absolu (ou pour la surcharge sans paramètre de base), puis la réduisent à une forme canonique dans la séquence suivante des étapes :

1. Chaque composant `X` de `is_symlink(X)` chemin pour `read_symlink(X)`lequel est **vrai** est remplacé par .

1. Chaque composant `.` de chemin (point est l’annuaire actuel établi par les composants précédents de voie) est supprimé.

1. Chaque paire de `X` / `..` composants de chemin (point-point est le répertoire parent établi par les composants de chemin précédents) est supprimé.

La fonction `pabs`revient alors .

## <a name="copy"></a><a name="copy"></a>Copie

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Les fonctions copient ou lient éventuellement un ou plusieurs fichiers de *à* *partir de* sous contrôle des *opts*, qui est pris comme `copy_options::none` pour les surcharges sans *paramètre opt.* *les opts* doivent contenir tout au plus l’un des :

- `skip_existing`, `overwrite_existing` ou `update_existing`

- `copy_symlinks` ou `skip_symlinks`

- `directories_only`, `create_symlinks` ou `create_hard_links`

Les fonctions déterminent d’abord `f` les `t` valeurs file_status pour *et* *pour*:

- si `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, en appelant`symlink_status`

- autrement, en appelant`status`

- Sinon, elles signalent une erreur.

Si `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, ils signalent alors une erreur (et ne font rien d’autre).

Sinon, `is_symlink(f)` si alors:

- Si `options & copy_options::skip_symlinks`, alors ne rien faire.

- Sinon, `!exists(t)&& options & copy_options::copy_symlinks`si `copy_symlink(from, to, opts)`, alors .

- Sinon, signalez une erreur.

Sinon, `is_regular_file(f)`si , alors:

- Si `opts & copy_options::directories_only`, alors ne rien faire.

- Sinon, `opts & copy_options::create_symlinks`si `create_symlink(to, from)`, alors .

- Sinon, `opts & copy_options::create_hard_links`si `create_hard_link(to, from)`, alors .

- Sinon, `is_directory(f)`si `copy_file(from, to`  /  `from.filename(), opts)`, alors .

- Sinon, valeur `copy_file(from, to, opts)`.

Sinon, `is_directory(f) && (opts & copy_options::recursive || !opts)`si , alors:

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

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Les fonctions copient toutes éventuellement le fichier *de à partir* `copy_options::none` de *sous* contrôle des *opts*, qui est pris comme pour les surcharges sans paramètre *opt.* *opts* doit contenir tout `skip_existing` `overwrite_existing`au `update_existing`plus l’un des , , , ou .

Si `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, puis signaler comme une erreur que le fichier existe déjà.

Sinon, `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`si , puis tenter de copier le contenu et les attributs du fichier *à partir du* fichier *à*. Signaler comme erreur si la tentative de copie échoue.

Les fonctions reviennent **vrai** si la copie est tentée et réussit, sinon **fausse**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si `is_directory(from)`, la `create_directory_symlink(from, to)`fonction appelle . Sinon, il `create_symlink(from, to)`appelle .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pour un nom de\/chemin\/tel qu’un b c, la fonction crée des répertoires a et un\/b au besoin afin qu’il puisse créer le répertoire un\/b\/c au besoin. Il revient **vrai** que si elle crée réellement le *pval*répertoire .

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La fonction crée le *pval répertoire* au besoin. Il retourne vrai que si elle crée réellement le *pval*répertoire , auquel cas il `perms::all` copie les autorisations de *l’attr*fichier existant , ou utilise pour les surcharges sans paramètre *attr.*

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien comme un lien avec l’annuaire *à*.

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien comme un lien dur vers l’annuaire ou le fichier *à*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée *un lien* comme un lien symlink vers le fichier *à*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Les fonctions sans paramètre *pval* retournent le nom de voie pour le répertoire actuel. Les autres fonctions ont placé l’annuaire actuel à *pval*.

## <a name="end"></a><a name="end"></a>Fin

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La première `directory_iterator()` fonction revient et la deuxième fonction revient`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Équivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Les fonctions ne reviennent **vraies** que si *gauche* et *droite* choisissent la même entité de système de fichiers.

## <a name="exists"></a><a name="exists"></a>Existe

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `status_known && stat.type() != file_not_found`. Les deuxième et troisième `exists(status(pval))`fonctions reviennent .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent la taille dans les octets `exists(pval) && is_regular_file(pval)` du fichier choisi par *pval,* si et la taille du fichier peut être déterminée. Sinon, ils signalent `uintmax_t(-1)`une erreur et le retour .

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La fonction renvoie le nombre de \-liens durs pour *le pval,* ou 1 si une erreur se produit.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La fonction retourne une `pval.native()`valeur de hachage pour .

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::block`. Les autres fonctions reviennent `is_block_file(status(pval))`.

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::character`. Les autres fonctions reviennent `is_character_file(status(pval))`.

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::directory`. Les autres fonctions reviennent `is_directory_file(status(pval))`.

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si, `is_directory(pval)`alors la `directory_iterator(pval) == directory_iterator()`fonction revient ; sinon il `file_size(pval) == 0`revient .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::fifo`. Les autres fonctions reviennent `is_fifo(status(pval))`.

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::other`. Les autres fonctions reviennent `is_other(status(pval))`.

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::regular`. Les autres fonctions reviennent `is_regular_file(status(pval))`.

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::socket`. Les autres fonctions reviennent `is_socket(status(pval))`.

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne `stat.type() == file_type::symlink`. Les autres fonctions reviennent `is_symlink(status(pval))`.

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Les deux premières fonctions renvoient l’heure de `file_time_type(-1)` la dernière modification des données pour *le pval,* ou si une erreur se produit. Les deux dernières fonctions fixent l’heure de la dernière modification des données pour *le pval* à *new_time*.

## <a name="permissions"></a><a name="permissions"></a>Autorisations

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Les fonctions fixent les autorisations pour le `mask & perms::mask` nom de `perms & (perms::add_perms | perms::remove_perms)`chemin choisi par *pval* à sous contrôle de . *masque* doit contenir tout `perms::add_perms` `perms::remove_perms`au plus un des et .

Si `mask & perms::add_perms`, les fonctions définissez les autorisations à `status(pval).permissions() | mask & perms::mask`. Sinon, `mask & perms::remove_perms`si , les fonctions `status(pval).permissions() & ~(mask & perms::mask)`définissez les autorisations à . Sinon, les fonctions fixent `mask & perms::mask`les autorisations à .

## <a name="proximate"></a><a name="proximate"></a>Immédiate

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Les fonctions signalent `path()` une `!is_symlink(pval)`erreur et reviennent si . Sinon, les fonctions retournent un objet de type `path` contenant le lien symbolique.

## <a name="relative"></a><a name="relative"></a>relatif

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>Retirer

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Les fonctions ne `exists(symlink_status(pval))` sont **valables** que si et le fichier est supprimé avec succès. Un lien symlink est lui-même supprimé, pas le fichier qu’il choisit.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si *le pval* est un répertoire, les fonctions suppriment de façon récursive toutes les entrées d’annuaire, puis l’entrée elle-même. Sinon, les fonctions appellent `remove`. Elles retournent un comptage de tous les éléments qui ont été supprimés.

## <a name="rename"></a><a name="rename"></a>Renommer

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Les fonctions renomment *de* *.* Un lien symlink est lui-même renommé, pas le fichier qu’il choisit.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Les fonctions modifient la taille d’un fichier de telle sorte que`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Espace

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La fonction renvoie des informations sur le volume `space_info`choisi par *pval*, dans une structure de type . La structure `uintmax_t(-1)` contient pour n’importe quelle valeur qui ne peut pas être déterminée.

## <a name="status"></a><a name="status"></a>Statut

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Les fonctions renvoient le statut de nom de chemin, le type de fichier, et les autorisations, associées au *pval.* Un lien symlink n’est pas lui-même testé, mais le fichier qu’il choisit.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La fonction revient`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Swap

```cpp
void swap(path& left, path& right) noexcept;
```

La fonction échange le contenu de *gauche* et *de droite.*

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Les fonctions renvoient l’état de symlink de nom de chemin, le type de fichier, et les autorisations, associés au *pval.* Les fonctions se `status(pval)` comportent de la même façon que, sauf qu’un lien symlink est lui-même testé, et non le fichier qu’il choisit.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Les fonctions retournent un nom de chemin absolu qui prend en compte si nécessaire le répertoire actuel associé au nom de sa racine. \(Pour POSIX, les `absolute(pval)`fonctions reviennent .\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Les fonctions retournent un nom de chemin pour un répertoire approprié à des fichiers conteneurs temporaires.

## <a name="u8path"></a><a name="u8path"></a>u8path u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

La première fonction se `path(source)` comporte de la même manière `path(first, last)` que la deuxième fonction se comporte de la même façon que, sauf que la source choisie dans chaque cas est prise comme une séquence d’éléments d’omble codé comme UTF-8, quel que soit le système de fichiers.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
