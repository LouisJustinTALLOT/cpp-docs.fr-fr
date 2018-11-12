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
ms.openlocfilehash: 513e393bbc782d87b37dab108428f2970fbb92e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644455"
---
# <a name="cnorowset-class"></a>CNoRowset, classe

Peut être utilisé comme argument template (`TRowset`) pour [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur. La valeur par défaut est `CAccessorBase`.

## <a name="remarks"></a>Notes

Utilisez `CNoRowset` comme argument de modèle si la commande ne renvoie pas un ensemble de lignes.

`CNoRowset` implémente les méthodes stub suivantes, chacune d’elles correspondent à d’autres méthodes de classe d’accesseur :

- `BindFinished` : Indique quand la liaison est terminée (retourne `S_OK`).

- `Close` -Libère des lignes et l’interface IRowset actuelle.

- `GetIID` -Récupère l’ID d’interface d’un point de connexion.

- `GetInterface` -Récupère une interface.

- `GetInterfacePtr` -Récupère un pointeur d’interface encapsulé.

- `SetAccessor` -Définit un pointeur vers l’accesseur.

- `SetupOptionalRowsetInterfaces` -Définit les interfaces facultatives pour l’ensemble de lignes.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)