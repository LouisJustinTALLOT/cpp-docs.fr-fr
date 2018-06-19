---
title: Recommandations relatives au choix entre ATL et MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 116f2066b98951aa2a470021f5527542ac8cbe46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357321"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recommandations relatives au choix entre ATL et MFC
Lorsque vous développez des applications et des composants, vous pouvez choisir entre deux méthodes — ATL et MFC (bibliothèque Microsoft Foundation Class).  
  
## <a name="using-atl"></a>À l’aide d’ATL  
 ATL est un moyen rapide et facile pour créer un composant COM en C++ et maintenir un faible encombrement mémoire. Utiliser ATL pour créer un contrôle, si vous n’avez pas besoin de toutes les fonctionnalités intégrées qui MFC fournit automatiquement.  
  
## <a name="using-mfc"></a>À l’aide de MFC  
 MFC vous permet de créer des applications complètes, des contrôles ActiveX et des documents actifs. Si vous avez déjà créé un contrôle avec MFC, vous souhaiterez continuer le développement avec MFC. Lorsque vous créez un nouveau contrôle, envisagez d’utiliser ATL si vous n’avez pas besoin de toutes les fonctionnalités intégrées de MFC.  
  
## <a name="using-atl-in-an-mfc-project"></a>À l’aide d’ATL dans un projet MFC  
 Vous pouvez ajouter la prise en charge pour l’utilisation des ATL dans un projet MFC existant en exécutant un Assistant. Pour plus d’informations, consultez [ajoutant la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à ATL](../atl/introduction-to-atl.md)

