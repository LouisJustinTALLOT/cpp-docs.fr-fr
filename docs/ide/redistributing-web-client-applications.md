---
title: Redistribution d’applications clientes web | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92bd843b24ee13b3d606ba8bb4f4f1cc265e8e5d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323194"
---
# <a name="redistributing-web-client-applications"></a>Redistribution d'applications clientes Web
Si votre application utilise les classes MFC implémentant le contrôle WebBrowser (par exemple `CHtmlView` ou `CHtmlEditView`), l’ordinateur cible doit disposer d’une installation de base de Microsoft Internet Explorer 4.0 ou ultérieur.  
  
 L’installation de la dernière version de Microsoft Internet Explorer garantit également que l’ordinateur cible dispose des derniers fichiers de contrôle communs.  
  
 Des informations relatives à l’installation des composants de base de Microsoft Internet Explorer sont disponibles dans l’article suivant de la Base de connaissances :  
  
-   Q185375, HOWTO: Create a Single EXE Install of Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 Vous trouverez les articles de la Base de connaissances dans MSDN Library ou sur [http://support.microsoft.com](http://support.microsoft.com).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)