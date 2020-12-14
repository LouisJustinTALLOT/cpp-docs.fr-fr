---
description: 'En savoir plus sur : classe Ccolumnaccessor,'
title: CColumnAccessor, classe
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 7551f39d34bb4f13b4ffae358db05aede2adb9e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335518"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor, classe

Génère du code de consommateur injecté.

## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Notes

Dans le code injecté, chaque colonne est liée comme un accesseur distinct. Vous devez savoir que cette classe est utilisée dans le code injecté (par exemple, vous pouvez la rencontrer lors du débogage), mais vous n’avez généralement jamais besoin de l’utiliser directement ou de ses méthodes.

`CColumnAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondant à des fonctionnalités à d’autres méthodes de la classe d’accesseur :

- `CColumnAccessor` Constructeur ; instancie et initialise l' `CColumnAccessor` objet.

- `CreateAccessor` Alloue de la mémoire pour les structures de liaison de colonne et initialise les membres de données de colonne.

- `BindColumns` Lie des colonnes à des accesseurs.

- `SetParameterBuffer` Alloue des mémoires tampons pour les paramètres.

- `AddParameter` Ajoute une entrée de paramètre aux structures d’entrée de paramètre.

- `HasOutputColumns` Détermine si l’accesseur a des colonnes de sortie

- `HasParameters` Détermine si l’accesseur a des paramètres.

- `BindParameters` Lie les paramètres créés aux colonnes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Informations de référence sur les modèles de consommateurs OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
