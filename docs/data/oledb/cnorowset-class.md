---
description: 'En savoir plus sur : classe Cnorowset,'
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
ms.openlocfilehash: 4cdb4631b63ec1f013183713900ffd9574d90fc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307559"
---
# <a name="cnorowset-class"></a>CNoRowset, classe

Peut être utilisé comme argument de modèle ( `TRowset` ) pour [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Paramètres

*TAccessor*<br/>
Classe d’accesseur. Par défaut, il s’agit de `CAccessorBase`.

## <a name="remarks"></a>Notes

`CNoRowset`À utiliser comme argument de modèle si la commande ne retourne pas d’ensemble de lignes.

`CNoRowset` implémente les méthodes stub suivantes, chacune d’elles correspondant à d’autres méthodes de la classe d’accesseur :

- `BindFinished` -Indique que la liaison est terminée (retourne `S_OK` ).

- `Close` -Libère les lignes et l’interface IRowset actuelle.

- `GetIID` -Récupère l’ID d’interface d’un point de connexion.

- `GetInterface` -Récupère une interface.

- `GetInterfacePtr` -Récupère un pointeur d’interface encapsulé.

- `SetAccessor` -Définit un pointeur vers l’accesseur.

- `SetupOptionalRowsetInterfaces` -Définit des interfaces facultatives pour l’ensemble de lignes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
