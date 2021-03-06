---
description: 'En savoir plus sur les éléments suivants : MFC et ATL'
title: MFC et ATL
ms.date: 01/24/2018
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
ms.topic: overview
ms.openlocfilehash: 9e21ebfa317f3d70e18fb8dd8cf77b80399f8f5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320090"
---
# <a name="mfc-and-atl"></a>MFC et ATL

MFC (Microsoft Foundation Classes) fournit un wrapper orienté objet C++ pour Win32 qui permet de développer rapidement des applications de bureau natives. La bibliothèque ATL (Active Template) est une bibliothèque de wrappers qui simplifie le développement COM. Elle est beaucoup utilisée pour créer des contrôles ActiveX.

Vous pouvez créer des programmes MFC ou ATL avec Visual Studio Community Edition ou une version supérieure. Les éditions Express ne prennent en charge ni MFC ni ATL.

Dans Visual Studio 2015, Visual C++ est un composant facultatif, et les composants MFC et ATL sont des sous-composants facultatifs sous Visual C++. Si vous ne sélectionnez pas ces composants lors de l’installation de Visual Studio, il vous est demandé de les installer la première fois que vous tentez de créer ou d’ouvrir un projet MFC ou ATL.

Dans Visual Studio 2017 et versions ultérieures, MFC et ATL sont des sous-composants facultatifs sous la charge de travail **développement Desktop avec C++** dans le programme Visual Studio installer. Vous pouvez installer la prise en charge ATL sans MFC, ou la prise en charge MFC et ATL combinée (MFC dépend de ATL). Pour plus d’informations sur les charges de travail et les composants, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="related-articles"></a>Articles connexes

|Titre|Description|
|-----------|-----------------|
|[Applications de bureau MFC](mfc-desktop-applications.md)|MFC (Microsoft Foundation Classes) propose un wrapper léger orienté objet via Win32 qui permet de développer rapidement des applications GUI en C++.|
|[Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)|ATL fournit des modèles de classe et d’autres constructions d’utilisation pour simplifier la création d’objets COM en C++.|
|[Classes partagées ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)|Références pour la [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) et d’autres classes partagées par MFC et ATL.|
|[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)|L’éditeur de ressources permet de modifier les ressources d’interface utilisateur telles que les chaînes, les images et les boîtes de dialogue.|
|[C++ dans Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Rubrique parente pour toute la documentation C++.|
