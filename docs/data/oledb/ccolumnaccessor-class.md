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
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212108"
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

- `CColumnAccessor` le constructeur ; instancie et initialise l’objet `CColumnAccessor`.

- `CreateAccessor` alloue de la mémoire pour les structures de liaison de colonne et initialise les membres de données de colonne.

- `BindColumns` lie les colonnes aux accesseurs.

- `SetParameterBuffer` alloue des tampons pour les paramètres.

- `AddParameter` ajoute une entrée de paramètre aux structures d’entrée de paramètre.

- `HasOutputColumns` détermine si l’accesseur a des colonnes de sortie

- `HasParameters` détermine si l’accesseur a des paramètres.

- `BindParameters` lie les paramètres créés aux colonnes.

## <a name="requirements"></a>Spécifications

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
