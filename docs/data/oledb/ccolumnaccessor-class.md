---
title: Ccolumnaccessor, classe | Documents Microsoft
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
ms.openlocfilehash: 8d211277a8354d94f1892b97ea8f808cc0b22c30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095318"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor, classe
Génère le code de consommateur injecté.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase  
```  
  
## <a name="remarks"></a>Notes  
 Dans le code injecté, chaque colonne est liée en tant qu’un accesseur séparé. Vous devez être conscient que cette classe est utilisée dans le code injecté (par exemple, vous pouvez rencontrer il lors du débogage), mais vous devez en général jamais directement l’utiliser ou ses méthodes.  
  
 `CColumnAccessor` implémente les méthodes stub suivantes, chacune d’elles correspondant de fonctionnalités à d’autres méthodes d’accesseur de classe :  
  
-   `CColumnAccessor` Le constructeur ; instancie et initialise le `CColumnAccessor` objet.  
  
-   `CreateAccessor` Alloue de la mémoire pour la colonne de structures de liaison et initialise les membres de données de colonne.  
  
-   **BindColumns** lie les colonnes aux accesseurs.  
  
-   **SetParameterBuffer** alloue des mémoires tampons pour les paramètres.  
  
-   `AddParameter` Ajoute une entrée de paramètre pour les structures d’entrée de paramètre.  
  
-   **HasOutputColumns** détermine si l’accesseur a des colonnes de sortie  
  
-   **HasParameters** détermine si l’accesseur a des paramètres.  
  
-   `BindParameters` Lie les paramètres aux colonnes.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)