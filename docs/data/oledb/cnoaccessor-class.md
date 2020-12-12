---
description: 'En savoir plus sur : classe Cnoaccessor,'
title: CNoAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: 624c72c841280ec56bacf0edd29efeb4b1005988
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170384"
---
# <a name="cnoaccessor-class"></a>CNoAccessor, classe

Peut être utilisé comme argument de modèle ( `TAccessor` ) pour les classes de modèle, telles que `CCommand` et `CTable` , qui requièrent un argument de classe d’accesseur.

## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Notes

Utilisez `CNoAccessor` comme argument template lorsque vous ne souhaitez pas que la classe prenne en charge les paramètres ou les colonnes de sortie.

`CNoAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondant à d’autres méthodes de la classe d’accesseur :

- `BindColumns` -Lie les colonnes aux accesseurs.

- `BindParameters` -Lie les paramètres créés aux colonnes.

- `Bind` -Crée des liaisons.

- `Close` -Ferme l’accesseur.

- `ReleaseAccessors` -Libère les accesseurs créés par la classe.

- `FreeRecordMemory` -Libère toutes les colonnes de l’enregistrement actif qui doivent être libérées.

- `GetColumnInfo` -Obtient les informations de colonne à partir de l’ensemble de lignes ouvert.

- `GetNumAccessors` -Récupère le nombre d’accesseurs créés par la classe.

- `IsAutoAccessor` -Retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.

- `GetHAccessor` -Récupère le handle d’accesseur d’un accesseur spécifié.

- `GetBuffer` -Récupère le pointeur vers la mémoire tampon du signet.

- `NoBindOnNullRowset` -Empêche la liaison de données sur les ensembles de lignes vides.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
