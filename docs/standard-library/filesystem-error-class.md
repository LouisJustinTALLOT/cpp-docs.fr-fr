---
title: filesystem_error, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: add1e0da43a44c35f39c96e8d65e36aeea0d3afb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405155"
---
# <a name="filesystemerror-class"></a>filesystem_error, classe

Classe de base pour toutes les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.

## <a name="syntax"></a>Syntaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Notes

La classe sert de classe de base pour toutes les exceptions levées afin de signaler une erreur dans des fonctions \<filesystem>. Il stocke un objet de type `string`, appelée `mymesg` ici aux fins de démonstration. Il stocke également deux objets de type `path`, appelé `mypval1` et `mypval2`.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[filesystem_error](#filesystem_error)|Construit un `filesystem_error` message.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[path1](#path1)|Retourne `mypval1`.|
|[path2](#path2)|Retourne `mypval2`.|
|[what](#what)|Retourne un pointeur vers `NTBS`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<filesystem >

**Espace de noms :** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error::filesystem_error

Le premier constructeur construit son message à partir de *what_arg* et *ec*. Le deuxième constructeur construit également son message à partir de *pval1*, qui est stockée dans `mypval1`. Le troisième constructeur construit également son message à partir de *pval1*, qui est stockée dans `mypval1`et à partir de *pval2*, qui est stockée dans `mypval2`.

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>Paramètres

*what_arg*<br/>
Message spécifié.

*ec*<br/>
Code d’erreur spécifié.

*mypval1*<br/>
Davantage de paramètre de message spécifié.

*mypval2*<br/>
Davantage de paramètre de message spécifié.

## <a name="path1"></a> filesystem_error::path1

La fonction membre retourne `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> filesystem_error::path2

La fonction membre retourne `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> filesystem_error::what

La fonction membre retourne un pointeur vers un `NTBS`, de préférence, composé à partir de, `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, et `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error, classe](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
