---
title: Fonctionnalités avancées, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: 1af16f7009ceb97ea86d641f47cf56ea5a398c26
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694294"
---
# <a name="advanced-features-mfc-application-wizard"></a>Fonctionnalités avancées, Assistant Application MFC

La rubrique répertorie les options de fonctionnalités supplémentaires de l’application, telles que l’aide, la prise en charge de l’impression, etc. Dans chaque section, spécifiez la prise en charge supplémentaire de ces fonctionnalités avancées.

- **Aide contextuelle (HTML)**

   Génère un ensemble de fichiers d’aide pour l’aide contextuelle, disponible à l’aide F1 et un menu d’aide, ou en cliquant sur un **aide** bouton sur une boîte de dialogue. La prise en charge de l'aide nécessite le compilateur d'aide. Si vous n'en disposez pas, vous pouvez l'installer en exécutant à nouveau le programme d'installation.

   Consultez [aide HTML : aide contextuelle pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) et [fichiers d’aide (aide HTML)](../../ide/help-files-html-help.md) pour plus d’informations.

- **Impression et Aperçu avant impression**

   Génère du code pour gérer l’impression, imprimer le programme d’installation et les commandes de l’aperçu avant impression en appelant les fonctions membres le [classe CView](../../mfc/reference/cview-class.md) à partir de la bibliothèque MFC. L'Assistant ajoute également des commandes pour ces fonctions au menu de l'application. Prise en charge de l’impression est disponible uniquement pour les applications qui spécifient **support de l’architecture Document/vue** dans le [Type d’Application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant. Par défaut, les applications à architecture Document/Vue disposent d'une prise en charge de l'impression.

- **Automation**

   Spécifie que l'application peut manipuler des objets implémentés dans une autre application ou expose l'application aux clients Automation.

- **Contrôles ActiveX**

   Prend en charge les contrôles ActiveX (valeur par défaut). Si vous ne pas Sélectionnez cette option et que vous souhaitez ultérieurement insérer des contrôles ActiveX dans votre projet, vous devez ajouter un appel à [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) de votre application [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) membre fonction.

- **MAPI (API de messagerie)**

   Spécifie que l'application peut créer, manipuler, transférer et stocker des messages électroniques.

- **Sockets Windows**

   Prend en charge Windows Sockets, que vous pouvez utiliser pour écrire des applications qui communiquent sur les réseaux TCP/IP.

- **Active Accessibility**

   Ajoute la prise en charge de [IAccessible](/windows/desktop/api/oleacc/nn-oleacc-iaccessible) à [CWnd](../../mfc/reference/cwnd-class.md)-les classes dérivées, qui vous permet de personnaliser l’interface utilisateur pour une meilleure interaction avec les clients d’accessibilité.

- **Manifeste des contrôles communs**

   Activé par défaut. Génère un manifeste d'application qui active la DLL de contrôles communs incluse dans Microsoft Windows XP et des systèmes d'exploitation plus récents.

   La version 6 de la DLL de contrôles communs ne met pas automatiquement à jour la version précédente des contrôles communs utilisée par vos applications existantes. Pour utiliser la version 6 de la DLL de contrôles communs, vous devez créer un manifeste d'application qui commande à votre application de charger la DLL. Cette DLL de contrôles communs prend également en charge les thèmes Windows XP.

   Un manifeste d'application peut également spécifier d'autres DLL et versions demandées par votre application. Pour plus d’informations sur les manifestes d’application, consultez [Applications isolées et les assemblys côte à côte](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) dans le SDK Windows.

- **Prise en charge le Gestionnaire de redémarrage**

   Ajoute la prise en charge pour le [Gestionnaire de redémarrage de Windows](/windows/desktop/RstMgr/using-restart-manager). Cette vidéo montre comment utiliser le Gestionnaire de redémarrage depuis MFC : [comment faire pour utiliser le nouveau Restart Manager](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100)).

- **Fenêtres frames avancées**

   |Option|Description|
   |------------|-----------------|
   |**Volet d’ancrage Explorateur**|Crée un volet d’ancrage qui ressemble à Visual Studio **l’Explorateur de solutions** à gauche de la fenêtre frame principale.|
   |**Trame d’ancrage sortie**|Crée un volet d’ancrage qui ressemble à Visual Studio **sortie** volet se trouve sous la fenêtre frame principale.|
   |**Volet d’ancrage propriétés**|Crée un volet d’ancrage qui ressemble à Visual Studio **propriétés** volet à droite de la fenêtre frame principale.|
   |**Volet de navigation**|Crée un volet d'ancrage qui ressemble à la barre de navigation Outlook et se trouve à gauche de la fenêtre frame principale.|
   |**Barre de légende**|Crée une barre de légende de style Office au-dessus de la fenêtre frame principale.|

- **Nombre de fichiers sur la liste des fichiers récents**

   Spécifie le nombre de fichiers à répertorier dans la liste des derniers fichiers utilisés. Le nombre par défaut est 4.

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

