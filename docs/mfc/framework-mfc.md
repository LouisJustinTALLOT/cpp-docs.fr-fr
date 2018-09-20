---
title: Framework (MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87db7b28ec340a76c074a7b32c0e182030042eeb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381957"
---
# <a name="framework-mfc"></a>Framework (MFC)

Votre travail avec l’infrastructure de la bibliothèque Microsoft Foundation classes (MFC) repose en grande partie sur quelques classes majeures et plusieurs outils Visual C++. Certaines classes encapsulent une grande partie de l’interface de programmation d’application (API) Win32. Autres classes encapsulent des concepts d’application tels que les documents, vues et l’application elle-même. D’autres encore encapsulent des fonctionnalités OLE et fonctionnalités d’accès aux données ODBC et DAO.

Par exemple, le concept de Win32 de fenêtre est encapsulée par classe MFC `CWnd`. Autrement dit, une classe C++ appelé `CWnd` encapsule ou « enveloppe » le `HWND` handle qui représente une fenêtre Windows. De même, la classe `CDialog` encapsule les boîtes de dialogue Win32.

L’encapsulation signifie que la classe C++ `CWnd`, par exemple, contient une variable membre de type `HWND`, et les fonctions membres de la classe encapsulent les appels aux fonctions Win32 qui prennent un `HWND` en tant que paramètre. Les fonctions membres de classe ont généralement le même nom que la fonction Win32 qu’elles encapsulent.

## <a name="in-this-section"></a>Dans cette section

[SDI et MDI](../mfc/sdi-and-mdi.md)

[Documents, vues et le Framework](../mfc/documents-views-and-the-framework.md)

[Assistants et les éditeurs de ressources](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>Sections connexes

[Génération à partir du Framework](../mfc/building-on-the-framework.md)

[Méthode d’appel de votre code par le Framework](../mfc/how-the-framework-calls-your-code.md)

[CWinApp : classe d’application](../mfc/cwinapp-the-application-class.md)

[Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)

[Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

[Objets fenêtre](../mfc/window-objects.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
