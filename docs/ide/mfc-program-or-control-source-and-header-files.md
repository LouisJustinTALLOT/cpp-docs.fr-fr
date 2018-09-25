---
title: Fichiers d’en-tête et fichiers sources de contrôle ou de programme MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cb9518f60db98bd590cecdffa09ee7d814241ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447906"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>Fichiers d'en-tête et fichiers sources de contrôle ou de programme MFC

Les fichiers suivants sont créés quand vous créez un projet MFC dans Visual Studio, selon les options que vous sélectionnez pour le projet que vous créez. Par exemple, votre projet contient les fichiers *NomProj*dlg.cpp et *NomProj*dlg.h seulement si vous créez un projet ou une classe basés sur des boîtes de dialogue.

Tous ces fichiers sont dans le répertoire *NomProj* ainsi que dans le dossier Header Files (fichiers .h) ou dans le dossier Source Files (fichiers .cpp) de l’Explorateur de solutions.

|Nom de fichier|Description|
|---------------|-----------------|
|*NomProj*.h|Le fichier include principal pour le programme ou la DLL. Il contient tous les symboles globaux et les directives `#include` pour les autres fichiers d’en-tête. Il dérive la classe `CPrjnameApp` de `CWinApp` et déclare une fonction membre `InitInstance`. Pour un contrôle, la classe `CPrjnameApp` est dérivée de `COleControlModule`.|
|*Projname*.cpp|Fichier source du programme principal. Il crée un objet de la classe `CPrjnameApp`, qui est dérivée de `CWinApp`, et remplace la fonction membre `InitInstance`.<br /><br /> Pour les exécutables, `CPrjnameApp::InitInstance` effectue plusieurs actions. Elle inscrit les modèles de document, qui servent de connexion entre les documents et les vues ; elle crée une fenêtre frame principale ; elle crée un document vide (ou ouvre un document s’il est spécifié comme argument de ligne de commande pour l’application).<br /><br /> Pour les DLL et les contrôles ActiveX (anciennement appelés OLE), `CProjNameApp::InitInstance` inscrit la fabrique d’objets du contrôle auprès d’OLE en appelant `COleObjectFactory::RegisterAll` et fait un appel à `AfxOLEInit`. En outre, la fonction membre `CProjNameApp::ExitInstance` est utilisée pour décharger le contrôle de la mémoire avec un appel à **AfxOleTerm**.<br /><br /> Ce fichier inscrit et désinscrit également le contrôle dans la base de données d’inscription de Windows en implémentant les fonctions `DllRegisterServer` et `DllUnregisterServer`.|
|*NomProj*ctrl.h, *NomProj*ctrl.cpp|Déclarez et implémentez la classe `CProjnameCtrl`. `CProjnameCtrl` est dérivé de `COleControl`, et des implémentations de structure de certaines fonctions membres sont définies pour initialiser, dessiner et sérialiser (charger et enregistrer) le contrôle. Des tables des messages, des événements et de dispatch sont également définies.|
|*NomProj*dlg.cpp, *NomProj*dlg.h|Créés si vous choisissez une application basée sur des boîtes de dialogue. Ces fichiers dérivent et implémentent la classe des boîtes de dialogue, nommée `CProjnameDlg`, et incluent les fonctions membres de structure pour initialiser une boîte de dialogue et effectuer l’échange des données de boîte de dialogue (DDX). Votre classe de la boîte de dialogue À propos est également placée dans ces fichiers au lieu de *NomProj*.cpp.|
|Dlgproxy.cpp, Dlgproxy.h|Dans un programme basé sur des boîtes de dialogue, le fichier d’implémentation et d’en-tête pour la classe de proxy Automation du projet pour la boîte de dialogue principale. Ceci est utilisé seulement si vous avez choisi la prise en charge d’Automation.|
|*NomProj*doc.cpp, *NomProj*doc.h|Dérivez et implémentez la classe de document nommée `CProjnameDoc`, et incluez les fonctions membres de structure pour initialiser un document, sérialiser (enregistrer et charger) un document, et implémenter les diagnostics du débogage.|
|*NomProj*set.h/.cpp|Créé si vous créez un programme qui prend en charge une base de données et contient la classe du recordset.|
|*NomProj*view.cpp, *NomProj*view.h|Dérivez et implémentez la classe d’affichage, nommée `CProjnameView`, qui est utilisée pour afficher et imprimer les données du document. La classe `CProjnameView` est dérivée d’une des classes MFC suivantes :<br /><br /> -   [CEditView](../mfc/reference/ceditview-class.md)<br />-   [CFormView](../mfc/reference/cformview-class.md)<br />-   [CRecordView](../mfc/reference/crecordview-class.md)<br />-   [COleDBRecordView](../mfc/reference/coledbrecordview-class.md)<br />-   [CTreeView](../mfc/reference/ctreeview-class.md)<br />-   [CListView](../mfc/reference/clistview-class.md)<br />-   [CRichEditView](../mfc/reference/cricheditview-class.md)<br />-   [CScrollView](../mfc/reference/cscrollview-class.md)<br />-   [CView](../mfc/reference/cview-class.md)<br />-   [CHTMLView](../mfc/reference/chtmlview-class.md)<br />-   [CHTMLEditView](../mfc/reference/chtmleditview-class.md)<br /><br /> La classe d’affichage du projet contient des fonctions membres de structure pour dessiner la vue et implémenter les diagnostics du débogage. Si vous avez activé la prise en charge de l’impression, des entrées de table des messages sont ajoutées pour les messages des commandes d’impression, de configuration de l’impression et d’aperçu avant impression. Ces entrées appellent les fonctions de membre correspondantes dans la classe d’affichage de base.|
|*NomProj*PropPage.h, *NomProj*PropPage.cpp|Déclarez et implémentez la classe `CProjnamePropPage`. `CProjnamePropPage` est dérivée de `COlePropertyPage` et une fonction membre de structure, `DoDataExchange`, est fournie pour implémenter l’échange et la validation des données.|
|IPframe.cpp, IPframe.h|Créés si l’option Mini-serveur ou Serveur complet est sélectionnée dans la page **Options Automation** (étape 3 sur 6) de l’Assistant Application. Les fichiers dérivent et implémentent la classe de fenêtre frame sur place, nommée **CInPlaceFrame**, utilisée quand le serveur est activé sur place par un programme conteneur.|
|Mainfrm.cpp, Mainfrm.h|Dérivez la classe **CMainFrame** de [CFrameWnd](../mfc/reference/cframewnd-class.md) (pour les applications SDI) ou de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) (pour les applications MDI). La classe **CMainFrame** gère la création de boutons de barre d’outils et de la barre d’état, si les options correspondantes sont sélectionnées dans la page **Options de l’application**  (étape 4 sur 6) de l’Assistant Application. Pour plus d’informations sur l’utilisation de **CMainFrame**, consultez [Classes de fenêtre Frame créées par l’Assistant Application](../mfc/frame-window-classes-created-by-the-application-wizard.md).|
|Childfrm.cpp, Childfrm.h|Dérivez la classe **CChildFrame** de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). La classe **CChildFrame** est utilisée pour les fenêtres frame de document MDI. Ces fichiers sont toujours créés si vous sélectionnez l’option MDI.|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Fichiers d’en-tête et fichiers sources de contrôle ou de programme ATL](../ide/atl-program-or-control-source-and-header-files.md)<br>
[Projets CLR](../ide/files-created-for-clr-projects.md)