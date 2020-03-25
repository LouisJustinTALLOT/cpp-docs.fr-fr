---
title: CNoRowset, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211469"
---
# <a name="cnorowset-class"></a>CNoRowset, classe

Peut être utilisé comme argument de modèle (`TRowset`) pour [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur. Par défaut, il s’agit de `CAccessorBase`.

## <a name="remarks"></a>Notes

Utilisez `CNoRowset` comme argument de modèle si la commande ne retourne pas d’ensemble de lignes.

`CNoRowset` implémente les méthodes stub suivantes, chacune d’elles correspondant à d’autres méthodes de la classe d’accesseur :

- `BindFinished` : indique à quel moment la liaison est terminée (retourne `S_OK`).

- `Close`-libère les lignes et l’interface IRowset actuelle.

- `GetIID` : récupère l’ID d’interface d’un point de connexion.

- `GetInterface` : récupère une interface.

- `GetInterfacePtr` : récupère un pointeur d’interface encapsulé.

- `SetAccessor`-définit un pointeur vers l’accesseur.

- `SetupOptionalRowsetInterfaces`-définit des interfaces facultatives pour l’ensemble de lignes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
