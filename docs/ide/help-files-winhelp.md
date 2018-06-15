---
title: Fichiers d’aide (WinHelp) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 505506c7f3a14a73c6b0c859a70938fee3eed69e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331543"
---
# <a name="help-files-winhelp"></a>Fichiers d'aide (WinHelp)
Les fichiers suivants sont créés quand vous ajoutez la prise en charge de l’aide de type WinHelp à votre application en cochant la case **Aide contextuelle**, puis en sélectionnant **Format WinHelp** dans la page [Fonctionnalités avancées](../mfc/reference/advanced-features-mfc-application-wizard.md) de l’Assistant Application MFC.  
  
|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|  
|---------------|------------------------|--------------------------------|-----------------|  
|*NomProj*.hpj|*NomProj*\hlp|Fichiers sources|Fichier projet d’aide utilisé par le compilateur d’aide pour créer le fichier d’aide de votre programme ou contrôle.|  
|*NomProj*.rtf|*NomProj*\hlp|Fichiers d’aide|Contient des rubriques de modèles que vous pouvez modifier et des informations sur la personnalisation de votre fichier .hpj.|  
|*NomProj*.cnt|*NomProj*\hlp|Fichiers d’aide|Fournit la structure de la fenêtre **Sommaire** dans l’aide de Windows.|  
|Makehelp.bat|*Projname*|Fichiers sources|Fichier utilisé par le système pour générer le projet d’aide lors de la compilation du projet.|  
|Print.rtf|*NomProj*\hlp|Fichiers d’aide|Fichier créé si votre projet offre une prise en charge de l’impression (option par défaut). Ce fichier décrit les commandes et boîtes de dialogue relatives à l’impression.|  
|*.bmp|*NomProj*\hlp|Fichiers de ressources|Contient les images des différentes rubriques d’aide générées.|  
  
 Vous pouvez ajouter la prise en charge de WinHelp à un projet de contrôle ActiveX MFC en sélectionnant **Générer des fichiers d’aide** sous l’onglet [Paramètres de l’application](../mfc/reference/application-settings-mfc-activex-control-wizard.md) de l’Assistant Contrôle ActiveX MFC. Les fichiers suivants sont ajoutés à votre projet quand vous ajoutez la prise en charge de l’aide à un contrôle ActiveX MFC :  
  
|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|  
|---------------|------------------------|--------------------------------|-----------------|  
|*NomProj*.hpj|*NomProj*\hlp|Fichiers sources|Fichier projet utilisé par le compilateur d’aide pour créer le fichier d’aide de votre programme ou contrôle.|  
|*NomProj*.rtf|*NomProj*\hlp|Projet|Contient des rubriques de modèles que vous pouvez modifier et des informations sur la personnalisation de votre fichier .hpj.|  
|Makehelp.bat|*Projname*|Fichiers sources|Fichier utilisé par le système pour générer le projet d’aide lors de la compilation du projet.|  
|Bullet.bmp|*Projname*|Fichiers de ressources|Fichier utilisé pour représenter les listes à puces dans les rubriques d’aide standard.|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)