---
description: 'En savoir plus sur : classe file_status'
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
ms.openlocfilehash: 8bc789d97f9b90b18214407fadab19e9644012a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324357"
---
# <a name="file_status-class"></a>file_status, classe

Encapsule un [file_type](../standard-library/filesystem-enumerations.md#file_type) et des [perms](../standard-library/filesystem-enumerations.md#perms) de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
class file_status;
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[file_status](#file_status)|Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et les autorisations [de fichier.](../standard-library/filesystem-enumerations.md#perms)|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[type](#type)|Obtient ou définit `file_type`.|
|[autorisations](#permissions)|Obtient ou définit les autorisations de fichiers.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_as)|Les opérateurs d’affectation de membre par défaut se comportent comme prévu.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<filesystem>

**Espace de noms :** std :: expérimental :: FileSystem, std :: expérimental :: FileSystem

## <a name="file_statusfile_status"></a><a name="file_status"></a> file_status :: file_status

Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et les autorisations [de fichier.](../standard-library/filesystem-enumerations.md#perms)

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Paramètres

*ftype*\
Spécifié `file_type` , la valeur par défaut est `file_type::none` .

*filtrage*\
Fichier spécifié `perms` , la valeur par défaut est `perms::unknown` .

*file_status*\
Objet stocké.

## <a name="file_statusoperator"></a><a name="op_as"></a> file_status :: Operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Paramètres

*file_status*\
[File_status](../standard-library/file-status-class.md) copié dans le `file_status` .

## <a name="type"></a>Type<a name="type"></a>

Obtient ou définit `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Paramètres

*ftype*\
`file_type` spécifié.

## <a name="permissions"></a><a name="permissions"></a> autorisations

Obtient ou définit les autorisations de fichiers.

Utilisez la méthode setter pour créer un fichier `readonly` ou supprimer l' `readonly` attribut.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Paramètres

*filtrage*\
`perms` spécifié.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Path, classe](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
