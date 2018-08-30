---
title: Services CWinApp spéciaux | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: beac10db09fefdf38d8e038855eb62ba8af80dbe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218610"
---
# <a name="special-cwinapp-services"></a>Services CWinApp spéciaux
Outre la boucle de message en cours d’exécution et vous donner la possibilité pour initialiser l’application et de nettoyer après cela, [CWinApp](../mfc/reference/cwinapp-class.md) fournit plusieurs autres services.  
  
##  <a name="_core_shell_registration"></a> Inscription du shell  
 Par défaut, l'Application MFC permet à l'utilisateur d'ouvrir les fichiers de données que votre application a créés en double-cliquant dessus dans l'Explorateur de fichiers ou le gestionnaire de fichiers. Si votre application est une application MDI et que vous spécifiez une extension pour les fichiers de votre application crée, l’Assistant Application MFC ajoute des appels à la [RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes) et [EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)fonctions membres de [CWinApp](../mfc/reference/cwinapp-class.md) à la `InitInstance` remplacement qu’il écrit pour vous.  
  
 `RegisterShellFileTypes` stocke les types de documents de votre application avec l'Explorateur de fichiers ou le gestionnaire de fichiers. La fonction ajoute des entrées à la base de données d'inscription que Windows gère. Les entrées enregistrent chaque type de document, associent une extension au type de fichier, spécifient une ligne de commande pour ouvrir l’application, puis spécifient une commande d’échange dynamique de données (DDE) pour ouvrir un document de ce type.  
  
 `EnableShellOpen` termine le processus permettant à l'application de recevoir des commandes DDE à partir de l'Explorateur de fichiers ou du gestionnaire de fichiers pour ouvrir le fichier choisi par l'utilisateur.  
  
 Cette prise en charge d'inscription automatique dans `CWinApp` élimine le besoin de fournir un fichier .reg à votre application ou d'exécuter un travail d'installation particulier.  
  
 Si vous souhaitez initialiser GDI + pour votre application (en appelant [GdiplusStartup](/windows/desktop/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup) dans votre [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) fonction), vous devez supprimer le thread d’arrière-plan GDI +.  
  
 Vous pouvez le faire en définissant le `SuppressBackgroundThread` membre de la [GdiplusStartupInput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput) structure **TRUE**. Quand supprimer GDI + d’arrière-plan thread, le `NotificationHook` et `NotificationUnhook` appels doivent être effectués uniquement avant entrant et sortant de boucle de message de l’application. Pour plus d’informations sur ces appels, consultez [GdiplusStartupOutput](/windows/desktop/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput). Par conséquent, un bon emplacement pour appeler `GdiplusStartup` et les fonctions de notification de raccordement serait dans une substitution de la fonction virtuelle [CWinApp::Run](../mfc/reference/cwinapp-class.md#run), comme illustré ci-dessous :  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]  
  
 Si vous ne supprimez pas le thread GDI+ d'arrière-plan, les commandes DDE peuvent être publiées prématurément dans l'application avant que la fenêtre principale soit créée. Les commandes DDE publiées par le shell peuvent être suspendues prématurément, ce qui aboutit à des messages d'erreur.  
  
##  <a name="_core_file_manager_drag_and_drop"></a> Fichier gestionnaire glisser -déplacer  
 Les fichiers peuvent être glissés de la fenêtre d'affichage des fichiers dans le gestionnaire de fichiers ou l'Explorateur de fichiers vers une fenêtre de votre application. Vous pouvez, par exemple, activer un ou plusieurs fichiers à faire glisser vers la fenêtre principale d'une application MDI, où l'application peut extraire le nom et les fenêtres enfants MDI ouverts pour ces fichiers.  
  
 Pour activer la fonction glisser-déplacer dans votre application, l’Assistant Application MFC écrit un appel à la [CWnd](../mfc/reference/cwnd-class.md) fonction membre [DragAcceptFiles](../mfc/reference/cwnd-class.md#dragacceptfiles) pour votre fenêtre frame principale dans votre `InitInstance`. Supprimez cet appel si vous ne souhaitez pas implémenter la fonctionnalité Glisser-déposer.  
  
> [!NOTE]
>  Vous pouvez également implémenter des fonctionnalités Glisser-déposer plus générales (comme faire glisser des données entre ou à l’intérieur de documents) avec OLE. Pour plus d’informations, consultez l’article [glisser-déposer (OLE)](../mfc/drag-and-drop-ole.md).  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> Suivi de la plupart des Documents utilisés récemment  
 Lorsque l'utilisateur ouvre et ferme des fichiers, l'objet d'application gère les quatre fichiers récemment utilisés. Les noms de ces fichiers sont ajoutés au menu Fichier et mis à jour lorsqu'ils sont modifiés. Le framework stocke ces noms de fichiers dans le Registre ou dans le fichier .ini, avec le même nom que le projet et les lit à partir du fichier au démarrage de votre application. Le `InitInstance` remplacer que l’Assistant Application MFC crée pour vous inclut un appel à la [CWinApp](../mfc/reference/cwinapp-class.md) fonction membre [LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings), ce qui charge des informations à partir du Registre ou le .ini fichier, y compris les derniers utilisé des noms de fichiers.  
  
 Ces entrées sont stockées comme suit :  
  
-   Dans Windows NT, Windows 2000 ou les versions ultérieures, la valeur est enregistrée dans une clé de Registre.  
  
-   Dans windows 3.x, la valeur est stockée dans le fichier WIN.INI.  
  
-   Dans Windows 95 et versions ultérieures, la valeur est stockée dans une version mise en cache du fichier WIN.INI.  
  
## <a name="see-also"></a>Voir aussi  
 [CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)