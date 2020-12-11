---
description: 'En savoir plus sur : recommandations pour le choix entre ATL et MFC'
title: Recommandations pour le choix entre ATL et MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: 506df04ebbd3bc9079e1d40cf14773d9d9a6bd1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159152"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recommandations pour le choix entre ATL et MFC

Lorsque vous développez des composants et des applications, vous pouvez choisir entre deux approches, à savoir ATL et MFC (le bibliothèque MFC (Microsoft Foundation Class)).

## <a name="using-atl"></a>Utilisation d’ATL

ATL est un moyen simple et rapide de créer un composant COM en C++ et de conserver un faible encombrement. Utilisez ATL pour créer un contrôle si vous n’avez pas besoin de toutes les fonctionnalités intégrées que MFC fournit automatiquement.

## <a name="using-mfc"></a>Utilisation de MFC

MFC vous permet de créer des applications complètes, des contrôles ActiveX et des documents actifs. Si vous avez déjà créé un contrôle avec MFC, vous souhaiterez peut-être continuer le développement dans MFC. Lorsque vous créez un nouveau contrôle, envisagez d’utiliser ATL si vous n’avez pas besoin de toutes les fonctionnalités intégrées de MFC.

## <a name="using-atl-in-an-mfc-project"></a>Utilisation d’ATL dans un projet MFC

Vous pouvez ajouter la prise en charge de l’utilisation d’ATL dans un projet MFC existant en exécutant un Assistant. Pour plus d’informations, consultez [Ajout de la prise en charge ATL à votre projet MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Voir aussi

[Introduction à ATL](../atl/introduction-to-atl.md)
