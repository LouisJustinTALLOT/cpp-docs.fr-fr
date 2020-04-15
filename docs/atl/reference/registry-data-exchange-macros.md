---
title: Macros d’échange de données de registre
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
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326069"
---
# <a name="registry-data-exchange-macros"></a>Macros d’échange de données de registre

Ces macros effectuent les opérations d’échange de données du Registre.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marque le début de la carte d’échange de données d’enregistrement.|
|[END_RDX_MAP](#end_rdx_map)|Marque la fin de la carte d’échange de données du registre.|
|[RDX_BINARY](#rdx_binary)|Associe l’inscription spécifiée au registre avec une variable de membre spécifiée de type BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type CString.|
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de registre spécifiée à une variable de membre spécifiée de type DWORD.|
|[RDX_TEXT](#rdx_text)|Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type TCHAR.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Marque le début de la carte d’échange de données d’enregistrement.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Notes

Les macros suivantes sont utilisées dans la carte d’échange de données du registre pour lire et écrire des entrées dans le registre du système :

|Macro|Description|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Associe l’inscription spécifiée au registre avec une variable de membre spécifiée de type BYTE.|
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de registre spécifiée à une variable de membre spécifiée de type DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type CString.|
|[RDX_TEXT](#rdx_text)|Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type TCHAR.|

La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créée par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisée chaque fois que votre code doit échanger des données entre le registre du système et les variables spécifiées dans la carte RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Marque la fin de la carte d’échange de données du registre.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Associe l’inscription spécifiée au registre avec une variable de membre spécifiée de type BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*rootkey*<br/>
La racine clé du registre.

*Sous-clé*<br/>
Le sous-clé du registre.

*Valuename*<br/>
La clé du registre.

*Membre*<br/>
La variable du membre pour s’associer à l’inscription spécifiée au registre.

*member_size*<br/>
La taille, dans les octets, de la variable du membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée en conjonction avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable de membre à une inscription donnée au registre. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créée par les macros BEGIN_RDX_MAP et END_RDX_MAP, devrait être utilisée pour effectuer l’échange de données entre le registre du système et les variables membres de la carte RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*rootkey*<br/>
La racine clé du registre.

*Sous-clé*<br/>
Le sous-clé du registre.

*Valuename*<br/>
La clé du registre.

*Membre*<br/>
La variable du membre pour s’associer à l’inscription spécifiée au registre.

*member_size*<br/>
La taille, dans les octets, de la variable du membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée en conjonction avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable de membre à une inscription donnée au registre. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créée par les macros BEGIN_RDX_MAP et END_RDX_MAP, devrait être utilisée pour effectuer l’échange de données entre le registre du système et les variables membres de la carte RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Associe l’entrée de registre spécifiée à une variable de membre spécifiée de type DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*rootkey*<br/>
La racine clé du registre.

*Sous-clé*<br/>
Le sous-clé du registre.

*Valuename*<br/>
La clé du registre.

*Membre*<br/>
La variable du membre pour s’associer à l’inscription spécifiée au registre.

*member_size*<br/>
La taille, dans les octets, de la variable du membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée en conjonction avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable de membre à une inscription donnée au registre. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créée par les macros BEGIN_RDX_MAP et END_RDX_MAP, devrait être utilisée pour effectuer l’échange de données entre le registre du système et les variables membres de la carte RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Associe l’inscription spécifiée au registre à une variable de membre spécifiée de type TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Paramètres

*rootkey*<br/>
La racine clé du registre.

*Sous-clé*<br/>
Le sous-clé du registre.

*Valuename*<br/>
La clé du registre.

*Membre*<br/>
La variable du membre pour s’associer à l’inscription spécifiée au registre.

*member_size*<br/>
La taille, dans les octets, de la variable du membre.

### <a name="remarks"></a>Notes

Cette macro est utilisée en conjonction avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable de membre à une inscription donnée au registre. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créée par les macros BEGIN_RDX_MAP et END_RDX_MAP, devrait être utilisée pour effectuer l’échange de données entre le registre du système et les variables membres de la carte RDX.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
