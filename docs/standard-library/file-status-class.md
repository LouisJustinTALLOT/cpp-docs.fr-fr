---
title: file_status, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 81ce4ecc1673087db8e985f94e297798dd712a6e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160015"
---
# <a name="filestatus-class"></a>file_status, classe

Encapsule un [file_type](../standard-library/filesystem-enumerations.md#file_type) et des [perms](../standard-library/filesystem-enumerations.md#perms) de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
class file_status;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[file_status](#file_status)|Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et fichier [perms](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[type](#type)|Obtient ou définit `file_type`.|
|[permissions](#permissions)|Obtient ou définit les autorisations de fichiers.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<filesystem >

**Namespace :** std::Experimental :: FileSystem, std::Experimental :: FileSystem

## <a name="file_status"></a> file_status::file_status

Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et fichier [perms](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Paramètres

*ftype*<br/>
Spécifié `file_type`, valeur par défaut est `file_type::none`.

*mask*<br/>
Fichier spécifié `perms`, valeur par défaut est `perms::unknown`.

*file_status*<br/>
L’objet stocké.

## <a name="op_as"></a> file_status::operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Paramètres

*file_status*<br/>
Le [file_status](../standard-library/file-status-class.md) copié dans le `file_status`.

## <a name="type"></a> Type

Obtient ou définit `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Paramètres

*ftype*<br/>
`file_type` spécifié.

## <a name="permissions"></a> Autorisations

Obtient ou définit les autorisations de fichiers.

Pour rendre un fichier, utilisez la méthode setter `readonly` ou supprimer le `readonly` attribut.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Paramètres

*mask*<br/>
`perms` spécifié.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[path, classe](../standard-library/path-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
