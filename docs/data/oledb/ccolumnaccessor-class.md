---
title: Ccolumnaccessor, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
dev_langs:
- C++
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b1843b6279cb7c86762cc6d975a2a7e67d3d278d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055635"
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