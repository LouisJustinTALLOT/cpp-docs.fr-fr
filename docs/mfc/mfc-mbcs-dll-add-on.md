---
title: MFC MBCS DLL, complément
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524816"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL, complément

Prise en charge de MFC et ses bibliothèques MBCS (jeu) de caractère multioctet nécessite une étape supplémentaire lors de l’installation de Visual Studio dans Visual Studio 2013 et versions ultérieures.

**Visual Studio 2013**: Par défaut, les bibliothèques MFC installés dans Visual Studio 2013 prennent uniquement en charge le développement d’Unicode. Vous avez besoin des DLL MBCS afin de générer un projet MFC dans Visual Studio 2013 a la **du jeu de caractères** propriété définie sur **utiliser le jeu de caractères multioctets** ou **Nenastaveno**. Téléchargez la DLL à [bibliothèque MFC multioctets pour Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770).

**Visual Studio 2015** : Unicode et MBCS des DLL MFC sont inclus dans les composants d’installation de Visual C++, mais prise en charge des MFC n’est pas installé par défaut. Visual C++ et MFC sont des configurations dont l’installation est facultative dans le programme d’installation de Visual Studio. Pour que MFC soit installé, choisissez **Personnalisé** dans le programme d’installation et, sous **Langages de programmation**, assurez-vous que **Visual C++** et **Microsoft Foundation Classes pour C++** sont sélectionnés. Si vous avez déjà installé Visual Studio, il vous est demandé d’installer Visual C++ et/ou MFC quand vous tentez de créer un projet MFC.

**Visual Studio 2017 et versions ultérieures** : Le Unicode et les DLL MFC MBCS sont installés avec le **développement Desktop en C++** charge de travail lorsque vous sélectionnez **prise en charge MFC et ATL** à partir de la **composants facultatifs** volet. Si votre installation n’inclut pas ces composants, accédez à la **fichier | Nouveaux projets** boîte de dialogue et cliquez sur le **ouvrir Visual Studio Installer** lien.

## <a name="see-also"></a>Voir aussi

[Versions de bibliothèque MFC](../mfc/mfc-library-versions.md)
