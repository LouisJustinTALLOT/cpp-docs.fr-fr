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
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457749"
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
|[file_status](#file_status)|Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et les [perms](../standard-library/filesystem-enumerations.md#perms)de fichier.|

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

**En-tête:** \<> de système de fichiers

**Espace de noms:** std:: expérimental:: FileSystem, std:: expérimental:: FileSystem

## <a name="file_status"></a>file_status::file_status

Construit un wrapper pour [file_type](../standard-library/filesystem-enumerations.md#file_type) et les [perms](../standard-library/filesystem-enumerations.md#perms)de fichier.

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
Spécifié `file_type`, la valeur par `file_type::none`défaut est.

*filtrage*\
Fichier `perms`spécifié, la valeur par `perms::unknown`défaut est.

*file_status*\
Objet stocké.

## <a name="op_as"></a>file_status:: Operator =

Les opérateurs d’affectation de membre par défaut se comportent comme prévu.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Paramètres

*file_status*\
[File_status](../standard-library/file-status-class.md) copié dans le `file_status`.

## <a name="type"></a>entrer

Obtient ou définit `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Paramètres

*ftype*\
`file_type` spécifié.

## <a name="permissions"></a>autorisations

Obtient ou définit les autorisations de fichiers.

Utilisez la méthode setter pour créer un `readonly` fichier ou supprimer `readonly` l’attribut.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Paramètres

*filtrage*\
`perms` spécifié.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Path, classe](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
