---
title: filesystem_error, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: c3dbfc080f0a1494950016f42189d932be05b0f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240741"
---
# <a name="filesystemerror-class"></a>filesystem_error, classe

Classe de base pour toutes les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.

## <a name="syntax"></a>Syntaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Notes

La classe sert de classe de base pour toutes les exceptions levées afin de signaler une erreur dans des fonctions \<filesystem>. Il stocke un objet de type `string`, appelée `mymesg` ici aux fins de démonstration. Il stocke également deux objets de type `path`, appelé `mypval1` et `mypval2`.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[filesystem_error](#filesystem_error)|Construit un `filesystem_error` message.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[path1](#path1)|Retourne `mypval1`.|
|[path2](#path2)|Retourne `mypval2`.|
|[what](#what)|Retourne un pointeur vers `NTBS`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<filesystem >

**Espace de noms :** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error

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

*what_arg*\
Message spécifié.

*EC*\
Code d’erreur spécifié.

*mypval1*\
Davantage de paramètre de message spécifié.

*mypval2*\
Davantage de paramètre de message spécifié.

## <a name="path1"></a> chemin1

La fonction membre retourne `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> chemin2

La fonction membre retourne `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> ce que

La fonction membre retourne un pointeur vers un `NTBS`, de préférence, composé à partir de, `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, et `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
