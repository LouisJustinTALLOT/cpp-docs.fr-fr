---
title: 2.4.3 unique construction | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db3f9ca834fb3f35c95732698fd02e16f31b4225
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690580"
---
# <a name="243-single-construct"></a>2.4.3 Construction simple
Le **unique** directive identifie une construction qui spécifie que le bloc structuré associé est exécuté par un seul thread de l’équipe (pas nécessairement le thread principal). La syntaxe de la **unique** la directive est la suivante :  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 La clause est une des opérations suivantes :  
  
 **privé (** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **copyprivate (** *variable-list* **)**  
  
 **nowait**  
  
 Il existe une barrière implicite après le **unique** construire, sauf si un **nowait** clause est spécifiée.  
  
 Restrictions à le **unique** directive sont les suivantes :  
  
-   Un seul **nowait** clause peut s’afficher dans un **unique** directive.  
  
-   Le **copyprivate** clause ne doit pas être utilisée avec le **nowait** clause.  
  
## <a name="cross-references"></a>Références externes :  
  
-   **privé**, **firstprivate**, et **copyprivate** clauses, consultez [Section 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) page 25.