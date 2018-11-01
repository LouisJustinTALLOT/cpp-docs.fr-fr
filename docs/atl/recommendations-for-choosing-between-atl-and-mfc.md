---
title: Recommandations relatives au choix entre ATL et MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: b3c01a54c1250ae97d5377cb0b1ff49a17c3f7c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468248"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recommandations relatives au choix entre ATL et MFC

Lorsque vous développez des applications et des composants, vous pouvez choisir entre deux approches — ATL et MFC (bibliothèque Microsoft Foundation Class).

## <a name="using-atl"></a>À l’aide de ATL

ATL est un moyen rapide et facile pour créer un composant COM dans C++ et maintenir un faible encombrement. Utilisez ATL pour créer un contrôle si vous n’avez pas besoin de toutes les fonctionnalités intégrées qui fournit automatiquement de MFC.

## <a name="using-mfc"></a>À l’aide de MFC

MFC vous permet de créer des applications complètes, des contrôles ActiveX et des documents actifs. Si vous avez déjà créé un contrôle avec MFC, voulez-vous continuer le développement avec MFC. Lorsque vous créez un nouveau contrôle, envisagez d’utiliser ATL si vous n’avez pas besoin de toutes les fonctionnalités intégrées de MFC.

## <a name="using-atl-in-an-mfc-project"></a>À l’aide de ATL dans un projet MFC

Vous pouvez ajouter la prise en charge pour l’utilisation d’ATL dans un projet MFC existant en exécutant un Assistant. Pour plus d’informations, consultez [Ajout de la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Voir aussi

[Introduction à ATL](../atl/introduction-to-atl.md)

