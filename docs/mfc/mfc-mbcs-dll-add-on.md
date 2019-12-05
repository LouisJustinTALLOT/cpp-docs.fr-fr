---
title: MFC MBCS DLL, complément
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810370"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL, complément

La prise en charge de MFC et de ses bibliothèques de jeux de caractères multioctets (MBCS) nécessite une étape supplémentaire lors de l’installation de Visual Studio dans Visual Studio 2013 et versions ultérieures.

**Visual Studio 2013**: par défaut, les bibliothèques MFC installées dans Visual Studio 2013 prennent uniquement en charge le développement Unicode. Vous avez besoin des dll MBCS pour pouvoir générer un projet MFC dans Visual Studio 2013 dont la propriété **jeu de caractères** est définie sur **utiliser le jeu de caractères multioctets** ou **non définie**. Téléchargez la DLL dans la [bibliothèque MFC multioctet pour Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015**: les DLL MFC Unicode et MBCS sont incluses dans les composants C++ d’installation visuelle, mais la prise en charge de MFC n’est pas installée par défaut. Visual C++ et MFC sont des configurations dont l’installation est facultative dans le programme d’installation de Visual Studio. Pour que MFC soit installé, choisissez **Personnalisé** dans le programme d’installation et, sous **Langages de programmation**, assurez-vous que **Visual C++** et **Microsoft Foundation Classes pour C++** sont sélectionnés. Si vous avez déjà installé Visual Studio, il vous est demandé d’installer Visual C++ et/ou MFC quand vous tentez de créer un projet MFC.

**Visual Studio 2017 et versions ultérieures**: les DLL MFC Unicode et MBCS sont installées avec le **développement bureautique avec C++**  charge de travail lorsque vous sélectionnez la **prise en charge de MFC et d’ATL** dans le volet **composants facultatifs** du programme Visual Studio installer. Si votre installation n’inclut pas ces composants, accédez au **fichier |** Boîte de dialogue nouveaux projets, puis cliquez sur le lien **ouvrir Visual Studio installer** . Pour plus d’informations, consultez [installer Visual Studio](/visualstudio/install/install-visual-studio).

## <a name="see-also"></a>Voir aussi

[Versions de bibliothèque MFC](../mfc/mfc-library-versions.md)
