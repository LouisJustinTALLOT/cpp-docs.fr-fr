---
description: 'En savoir plus sur : classe filesystem_error'
title: filesystem_error, classe
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 8165bfbc0d59dbbdab17d910e2e2f7973988049d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232432"
---
# <a name="filesystem_error-class"></a>filesystem_error, classe

Classe de base pour toutes les exceptions qui sont levées pour signaler un dépassement de capacité du système de bas niveau.

## <a name="syntax"></a>Syntaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Notes

La classe sert de classe de base pour toutes les exceptions levées pour signaler une erreur dans les \<filesystem> fonctions. Il stocke un objet de type `string` , appelé `mymesg` ici pour les besoins de l’exposition. Il stocke également deux objets de type `path` , appelés `mypval1` et `mypval2` .

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[filesystem_error](#filesystem_error)|Construit un `filesystem_error` message.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[chemin1](#path1)|Retourne `mypval1`.|
|[chemin2](#path2)|Retourne `mypval2`.|
|[données](#what)|Retourne un pointeur vers `NTBS`.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<filesystem>

**Espace de noms :** std::experimental::filesystem

## <a name="filesystem_error"></a><a name="filesystem_error"></a> filesystem_error

Le premier constructeur construit son message à partir de *what_arg* et *EC*. Le deuxième constructeur construit également son message à partir de *pval1*, qu’il stocke dans `mypval1` . Le troisième constructeur construit également son message à partir de *pval1*, qu’il stocke dans `mypval1` et à partir de *pval2*, qu’il stocke dans `mypval2` .

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
Paramètre de message spécifié supplémentaire.

*mypval2*\
Paramètre de message spécifié supplémentaire.

## <a name="path1"></a><a name="path1"></a> chemin1

La fonction membre retourne `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a><a name="path2"></a> chemin2

La fonction membre retourne `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a><a name="what"></a> données

La fonction membre retourne un pointeur vers un `NTBS` , de préférence composé de,,, `runtime_error::what()` `system_error::what()` `mymesg` `mypval1.native_string()` et `mypval2.native_string()` .

```cpp
const char *what() const noexcept;
```
