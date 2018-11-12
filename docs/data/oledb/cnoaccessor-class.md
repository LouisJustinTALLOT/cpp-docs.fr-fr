---
title: CNoAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: d6eb5aaa9a66f46335b0a364e6c6e79abc297d64
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647890"
---
# <a name="cnoaccessor-class"></a>CNoAccessor, classe

Peut être utilisé comme argument template (`TAccessor`) pour les classes de modèle, tel que `CCommand` et `CTable`, qui nécessitent un argument de classe d’accesseur.

## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Notes

Utilisez `CNoAccessor` comme argument de modèle lorsque vous ne souhaitez pas que la classe pour prendre en charge des paramètres ou des colonnes de sortie.

`CNoAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondent à d’autres méthodes de classe d’accesseur :

- `BindColumns` -Lie les colonnes aux accesseurs.

- `BindParameters` -Lie les paramètres créés pour les colonnes.

- `Bind` -Crée des liaisons.

- `Close` -Ferme l’accesseur.

- `ReleaseAccessors` -Libère les accesseurs créés par la classe.

- `FreeRecordMemory` -Libère toutes les colonnes dans l’enregistrement actif qui doivent être libérées.

- `GetColumnInfo` -Obtient les informations de colonne à partir de l’ensemble de lignes ouvert.

- `GetNumAccessors` -Récupère le nombre d’accesseurs créé par la classe.

- `IsAutoAccessor` -Retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.

- `GetHAccessor` -Récupère le handle d’accesseur d’un accesseur spécifié.

- `GetBuffer` -Récupère le pointeur vers la mémoire tampon de signet.

- `NoBindOnNullRowset` : Empêche la liaison de données sur des ensembles de lignes vide.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)