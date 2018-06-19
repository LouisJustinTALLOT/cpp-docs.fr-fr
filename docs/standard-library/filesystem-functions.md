---
title: '&lt;filesystem&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: bfe07904a8eec87fb18441b92096d8ba6b72e4e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848659"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt;, fonctions

Ces fonctions libres de l’en-tête [\<filesystem>](../standard-library/filesystem.md) effectuent des opérations de modification et de requête sur des chemins, des fichiers, des liens symboliques, des répertoires et des volumes. Pour plus d’informations et pour obtenir des exemples de code, consultez [Navigation dans le système de fichiers (C++)](../standard-library/file-system-navigation.md).
||||
|-|-|-|
|[absolute](#absolute)|[begin](#begin)|[canonical](#canonical)|
|[copy](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[end](#end)|[equivalent](#equivalent)|[exists](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[permissions](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[rename](#rename)|
|[resize_file](#resize_file)|[space](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name=""></a>  <a name="absolute"></a> absolute

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La fonction retourne le chemin absolu correspondant au `pval` relatif à l’objet `base` du chemin :

1. Si pval.has_root_name() && pval.has_root_directory(), la fonction retourne pval.

1. Si pval.has_root_name() && !pval.has_root_directory(), la fonction retourne pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path().

1. Si !pval.has_root_name() && pval.has_root_directory(), la fonction retourne absolute(base).root_name() / pval.

1. Si !pval.has_root_name() && !pval.has_root_directory(), la fonction retourne absolute(base) / pval.

## <a name="begin"></a>  begin

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Les deux fonctions retournent `iter`.

## <a name="canonical"></a>  canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Les fonctions forment toutes un nom de chemin absolu pabs = absolute(pval, base) (ou pabs = absolute(pval) pour la surcharge sans paramètre base), puis le réduisent à une forme canonique dans la séquence d’étapes suivante :

1. Chaque composant X du chemin pour lequel is_symlink(X) est true est remplacé par read_symlink(X).

1. Chaque composant du chemin. (point [dot] est le répertoire actuel établi par les composants du chemin précédent) est supprimé.

1. Chaque paire de composants du chemin X/.. (point-point [dot-dot] est le répertoire parent établi par les composants du chemin précédent) est supprimée.

La fonction retourne alors pabs.

## <a name="copy"></a>  copy

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Les fonctions sont toutes susceptibles de copier ou de lier un ou plusieurs fichiers à partir de `from` dans `to` sous le contrôle de `opts`, qui est pris comme copy_options::none pour les surcharges sans paramètre `opts`. `opts` contient au maximum un des éléments suivants :

- skip_existing, overwrite_existing ou update_existing

- copy_symlinks ou skip_symlinks

- directories_only, create_symlinks ou create_hard_links

Les fonctions déterminent d’abord les valeurs de file_status f pour `from` et t pour `to` :

- si opts & (copy_options::create_symlinks &#124; copy_options::skip_symlinks), en appelant symlink_status

- sinon, en appelant status

- Sinon, elles signalent une erreur.

Si !exists(f) &#124;&#124; equivalent(f, t) &#124;&#124; is_other(f) &#124;&#124; is_other(t) &#124;&#124; is_directory(f)&& is_regular_file(t), elles signalent une erreur (et n’effectuent aucune autre opération).

Sinon, si is_symlink(f) :

- Si options & copy_options::skip_symlinks, ne rien faire.

- Sinon, si !exists(t)&& options & copy_options::copy_symlinks, copy_symlink(from, to, opts).

- Sinon, elles signalent une erreur.

Sinon, si is_regular_file(f) :

- Si opts & copy_options::directories_only, ne rien faire.

- Sinon, si opts & copy_options::create_symlinks, create_symlink(to, from).

- Sinon, si opts & copy_options::create_hard_links, create_hard_link(to, from).

- Sinon, si is_directory(f), copy_file(from, to / from.filename(), opts).

- Sinon, copy_file(from, to, opts).

Sinon, si is_directory(f) && (opts & copy_options::recursive &#124;&#124; !opts) :

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

## <a name="opy_file"></a>  copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Les fonctions sont toutes susceptibles de copier le fichier à partir de `from` dans `to` sous le contrôle de `opts`, qui est pris comme copy_options::none pour les surcharges sans paramètre `opts`. `opts` contient au maximum un élément skip_existing, overwrite_existing ou update_existing.

Si exists\(to\) && \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\)\), signaler comme une erreur le fait que le fichier existe déjà.

Sinon, si \!exists\(to\) &#124;&#124; opts & copy_options::overwrite_existing &#124;&#124; opts & copy_options::update_existing&& last_write_time\(to\) \< last_write_time\(from\) &#124;&#124; \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options:update_existing\)\), essayer de copier le contenu et les attributs du fichier from dans le fichier to. Signaler comme erreur si la tentative de copie échoue.

Les fonctions retournent true (vrai) si la copie est tentée et qu’elle réussit, sinon false (faux).

## <a name="copy_symlink "></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si is_directory\(from\) la fonction appelle create_directory_symlink\(from, to\). Sinon, elle appelle create_symlink\(from, to\).

## <a name="create_directories"></a>  create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pour un chemin comme a\/b\/c, la fonction crée si nécessaire les répertoires a et a\/b pour pouvoir créer le répertoire a\/b\/c, si nécessaire. Elle retourne true seulement si elle crée réellement le répertoire `pval`.

## <a name="create_directory"></a>  create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La fonction crée le répertoire `pval`, si nécessaire. Elle retourne true seulement si elle crée réellement le répertoire `pval`, auquel cas elle copie les autorisations du fichier `attr` existant ou elle utilise perms::all pour les surcharges sans paramètre `attr`.

## <a name="create_directory_symlink "></a>  create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien sous forme de lien symbolique vers le répertoire `to`.

## <a name="create_hard_link"></a>  create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée un lien sous forme de lien physique vers le répertoire ou le fichier `to`.

## <a name="create_symlink "></a>  create_symlink

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La fonction crée `link` sous forme de lien symbolique vers le fichier `to`.

## <a name="current_path"></a>  current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Les fonctions sans paramètre `pval` retournent le chemin du répertoire actuel. Les autres fonctions définissent le répertoire actuel sur `pval`.

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La première fonction retourne directory_iterator\(\) et la deuxième fonction retourne recursive_directory_iterator\(\)

## <a name="equivalent"></a>  equivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Les fonctions retournent true seulement si `left` et `right` désignent la même entité filesystem.

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne status_known && stat.type\(\) \!\= file_not_found. Les deuxième et troisième fonctions retournent exists\(status\(pval\)\).

## <a name="file_size"></a>  file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent la taille en octets du fichier désigné par `pval`, si exists\(pval\) && is_regular_file\(pval\) et que la taille du fichier peut être déterminée. Sinon, elles signalent une erreur et retournent uintmax_t\(\-1\).

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La fonction retourne le nombre de liens physiques pour `pval`, ou \-1 si une erreur se produit.

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La fonction retourne une valeur de hachage pour pval.native\(\).

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::block. Les autres fonctions retournent is_block_file\(status\(pval\)\).

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::character. Les autres fonctions retournent is_character_file\(status\(pval\)\).

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::directory. Les autres fonctions retournent is_directory_file\(status\(pval\)\).

## <a name="is_empty"></a>  is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si is_directory\(pval\), la fonction retourne directory_iterator\(pval\) \=\= directory_iterator\(\) ; sinon elle retourne file_size\(pval\) \=\= 0.

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::fifo. Les autres fonctions retournent is_fifo\(status\(pval\)\).

## <a name="is_other"></a>  is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::other. Les autres fonctions retournent is_other\(status\(pval\)\).

## <a name="s_regular_file"></a>  is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::regular. Les autres fonctions retournent is_regular_file\(status\(pval\)\).

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::socket. Les autres fonctions retournent is_socket\(status\(pval\)\).

## <a name="is_symlink"></a>  is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La première fonction retourne stat.type\(\) \=\= file_type::symlink. Les autres fonctions retournent is_symlink\(status\(pval\)\).

## <a name="last_write_time"></a>  last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Les deux premières fonctions retournent la date/heure de la dernière modification des données pour `pval`, ou file_time_type\(\-1\) si une erreur se produit. Les deux dernières fonctions définissent la date/heure de la dernière modification des données pour `pval` sur new_time.

## <a name="permissions"></a>  permissions

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Les fonctions définissent les autorisations du chemin désigné par `pval` sur mask & perms::mask sous le contrôle de perms & \(perms::add_perms &#124; perms::remove_perms\). mask contiendra au plus un des éléments perms::add_perms et perms::remove_perms.

Si mask & perms::add_perms, les fonctions définissent les autorisations sur status\(pval\).permissions\(\) &#124; mask & perms::mask. Sinon, si mask & perms::remove_perms, les fonctions définissent les autorisations sur status\(pval\).permissions\(\) & ~\(mask & perms::mask\). Sinon, les fonctions définissent les autorisations sur mask & perms::mask.

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Les fonctions signalent une erreur et retournent path\(\) si \!is_symlink\(pval\). Sinon, les fonctions retournent un objet de type `path` contenant le lien symbolique.

## <a name="remove"></a>  remove

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent true seulement si exists\(symlink_status\(pval\)\) et que le fichier est supprimé. Un lien symbolique est lui-même supprimé, mais pas le fichier qu’il désigne.

## <a name="remove_all"></a>  remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si `pval` est un répertoire, les fonctions suppriment de façon récursive toutes les entrées de répertoire, puis l’entrée elle-même. Sinon, les fonctions appellent remove. Elles retournent un comptage de tous les éléments qui ont été supprimés.

## <a name="rename"></a>  rename

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

Les fonctions renomment `from` en `to`. Un lien symbolique est lui-même renommé, mais pas le fichier qu’il désigne.

## <a name="resize_file"></a>  resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Les fonctions modifient la taille d’un fichier de sorte que file_size\(pval\) \=\= size

## <a name="space"></a>  space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La fonction retourne des informations sur le volume désigné par `pval`, dans une structure de type `space_info`. La structure contient uintmax_t\(\-1\) pour les valeurs qui ne peuvent pas être déterminées.

## <a name="status"></a>  status

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Les fonctions retournent l’état du chemin, le type de fichier et les autorisations associés à `pval`. Le lien symbolique n’est pas vérifié, contrairement au fichier qu’il désigne.

## <a name="status_known"></a>  status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La fonction retourne stat.type\(\) \!\= file_type::none

## <a name="swap"></a>  swap

```cpp
void swap(path& left, path& right) noexcept;
```

La fonction échange le contenu de `left` et `right`.

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Les fonctions retournent l’état du lien symbolique du chemin, le type de fichier et les autorisations associés à `pval`. Les fonctions se comportent de la même façon que status\(pval\), excepté que le lien symbolique est vérifié, mais pas le fichier qu’il désigne.

## <a name="system_complete"></a>  system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Les fonctions retournent un nom de chemin absolu qui prend en compte si nécessaire le répertoire actuel associé au nom de sa racine. \(Pour Posix, les fonctions retournent absolute\(pval\).\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Les fonctions retournent un nom de chemin pour un répertoire approprié à des fichiers conteneurs temporaires.

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

La première fonction se comporte comme path(source) et la seconde fonction se comporte comme path(first, last), excepté que la source désignée dans chaque cas est prise comme une séquence d’éléments char encodés en UTF-8, quel que soit le système de fichiers.


