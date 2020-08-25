---
title: Macros d’échange de données de Registre
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: 507db77b525c526fe1cd47c7d75c34e15a6a0628
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834542"
---
# <a name="registry-data-exchange-macros"></a>Macros d’échange de données de Registre

Ces macros effectuent des opérations d’échange de données de registre.

|Nom|Description|
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marque le début de la carte d’échange de données du Registre.|
|[END_RDX_MAP](#end_rdx_map)|Marque la fin du mappage d’échange de données du Registre.|
|[RDX_BINARY](#rdx_binary)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type CString.|
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type DWORD.|
|[RDX_TEXT](#rdx_text)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type TCHAR.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlplus. h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a> BEGIN_RDX_MAP

Marque le début de la carte d’échange de données du Registre.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Notes

Les macros suivantes sont utilisées dans le mappage d’échange de données du Registre pour lire et écrire des entrées dans le registre système :

|Macro|Description|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type BYTE.|
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type CString.|
|[RDX_TEXT](#rdx_text)|Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type TCHAR.|

La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre portant le même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée chaque fois que votre code a besoin d’échanger des données entre le registre système et les variables spécifiées dans le mappage RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a> END_RDX_MAP

Marque la fin du mappage d’échange de données du Registre.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a> RDX_BINARY

Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*CLE_PRINCIPALE*<br/>
Racine de la clé de registre.

*sous-clé*<br/>
Sous-clé du Registre.

*valueName*<br/>
Clé de registre.

*membre*<br/>
Variable membre à associer à l’entrée de Registre spécifiée.

*member_size*<br/>
Taille, en octets, de la variable membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée pour effectuer l’échange de données entre le registre système et les variables membres de la carte RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a> RDX_CSTRING_TEXT

Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*CLE_PRINCIPALE*<br/>
Racine de la clé de registre.

*sous-clé*<br/>
Sous-clé du Registre.

*valueName*<br/>
Clé de registre.

*membre*<br/>
Variable membre à associer à l’entrée de Registre spécifiée.

*member_size*<br/>
Taille, en octets, de la variable membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée pour effectuer l’échange de données entre le registre système et les variables membres de la carte RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a> RDX_DWORD

Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*CLE_PRINCIPALE*<br/>
Racine de la clé de registre.

*sous-clé*<br/>
Sous-clé du Registre.

*valueName*<br/>
Clé de registre.

*membre*<br/>
Variable membre à associer à l’entrée de Registre spécifiée.

*member_size*<br/>
Taille, en octets, de la variable membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée pour effectuer l’échange de données entre le registre système et les variables membres de la carte RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a> RDX_TEXT

Associe l’entrée de Registre spécifiée à une variable membre spécifiée de type TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*CLE_PRINCIPALE*<br/>
Racine de la clé de registre.

*sous-clé*<br/>
Sous-clé du Registre.

*valueName*<br/>
Clé de registre.

*membre*<br/>
Variable membre à associer à l’entrée de Registre spécifiée.

*member_size*<br/>
Taille, en octets, de la variable membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée pour effectuer l’échange de données entre le registre système et les variables membres de la carte RDX.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
