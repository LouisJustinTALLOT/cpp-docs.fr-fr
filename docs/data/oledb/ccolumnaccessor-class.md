---
title: CColumnAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 85d3d9d4339634ea7948d7d5e9e09725b7fd8758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611365"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor, classe

Génère du code de consommateur injecté.

## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Notes

Dans le code injecté, chaque colonne est lié en tant qu’un accesseur séparé. Vous devez être conscient que cette classe est utilisée dans le code injecté (par exemple, vous pouvez rencontrer il lors du débogage), mais vous devez en général jamais l’utiliser directement ou ses méthodes.

`CColumnAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondent dans les fonctionnalités à d’autres méthodes de classe d’accesseur :

- `CColumnAccessor` Le constructeur ; instancie et initialise le `CColumnAccessor` objet.

- `CreateAccessor` Alloue de la mémoire pour la colonne des structures de liaison et initialise les membres de données de colonne.

- `BindColumns` Lie les colonnes aux accesseurs.

- `SetParameterBuffer` Alloue des tampons de paramètres.

- `AddParameter` Ajoute une entrée de paramètre pour les structures d’entrée de paramètre.

- `HasOutputColumns` Détermine si l’accesseur a des colonnes de sortie

- `HasParameters` Détermine si l’accesseur a des paramètres.

- `BindParameters` Lie les paramètres créés pour les colonnes.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)