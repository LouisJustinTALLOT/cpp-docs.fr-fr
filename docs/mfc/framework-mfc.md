---
description: 'En savoir plus sur : Framework (MFC)'
title: Framework (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: 12e5a28e231dfadec867213ebf1cea6fd6ae7300
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193485"
---
# <a name="framework-mfc"></a>Framework (MFC)

Votre travail avec l’infrastructure de bibliothèque MFC (Microsoft Foundation Class) repose en grande partie sur quelques classes majeures et plusieurs outils de Visual C++. Certaines classes encapsulent une grande partie de l’interface de programmation d’applications (API) Win32. D’autres classes encapsulent des concepts d’application tels que des documents, des vues et l’application elle-même. D’autres encore encapsulent les fonctionnalités OLE et les fonctionnalités d’accès aux données ODBC et DAO.  (DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.)

Par exemple, Win32 concept de fenêtre est encapsulé par la classe MFC `CWnd` . Autrement dit, une classe C++ appelée `CWnd` encapsule ou « encapsule » le `HWND` handle qui représente une fenêtre Windows. De même, la classe `CDialog` encapsule les boîtes de dialogue Win32.

L’encapsulation signifie que la classe C++ `CWnd` , par exemple, contient une variable membre de type `HWND` , et que les fonctions membres de la classe encapsulent les appels aux fonctions Win32 qui acceptent un `HWND` comme paramètre. Les fonctions membres de classe ont généralement le même nom que la fonction Win32 qu’elles encapsulent.

## <a name="in-this-section"></a>Dans cette section

[SDI et MDI](sdi-and-mdi.md)

[Documents, vues et le Framework](documents-views-and-the-framework.md)

[Assistants et éditeurs de ressources](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>Dans les sections connexes

[Génération sur le Framework](building-on-the-framework.md)

[Comment le Framework appelle votre code](how-the-framework-calls-your-code.md)

[CWinApp : classe d’application](cwinapp-the-application-class.md)

[Modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md)

[Gestion et mappage des messages](message-handling-and-mapping.md)

[Objets de fenêtre](window-objects.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour écrire des applications pour Windows](using-the-classes-to-write-applications-for-windows.md)
