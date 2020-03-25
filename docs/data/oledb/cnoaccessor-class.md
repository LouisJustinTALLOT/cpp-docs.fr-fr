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
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211729"
---
# <a name="cnoaccessor-class"></a>CNoAccessor, classe

Peut être utilisé comme argument de modèle (`TAccessor`) pour les classes de modèle, telles que `CCommand` et `CTable`, qui requièrent un argument de classe d’accesseur.

## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Notes

Utilisez `CNoAccessor` comme argument template quand vous ne souhaitez pas que la classe prenne en charge les paramètres ou les colonnes de sortie.

`CNoAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondant à d’autres méthodes de la classe d’accesseur :

- `BindColumns`-lie les colonnes aux accesseurs.

- `BindParameters`-lie les paramètres créés aux colonnes.

- `Bind` : crée des liaisons.

- `Close`-ferme l’accesseur.

- `ReleaseAccessors` : libère les accesseurs créés par la classe.

- `FreeRecordMemory`-libère toutes les colonnes de l’enregistrement actif qui doivent être libérées.

- `GetColumnInfo`-obtient des informations sur les colonnes à partir de l’ensemble de lignes ouvert.

- `GetNumAccessors` : récupère le nombre d’accesseurs créés par la classe.

- `IsAutoAccessor`-retourne la valeur true si les données sont récupérées automatiquement pour l’accesseur pendant une opération de déplacement.

- `GetHAccessor` : récupère le handle d’accesseur d’un accesseur spécifié.

- `GetBuffer` : récupère le pointeur vers la mémoire tampon de signet.

- `NoBindOnNullRowset`-empêche la liaison de données sur les ensembles de lignes vides.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
