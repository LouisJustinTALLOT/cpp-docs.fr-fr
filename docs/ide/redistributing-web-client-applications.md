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
ms.openlocfilehash: d036f7d46e0db84b8572b26c747947c929972517
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889930"
---
# <a name="redistributing-web-client-applications"></a>Redistribution d'applications clientes Web

Si votre application utilise les classes MFC implémentant le contrôle WebBrowser (par exemple `CHtmlView` ou `CHtmlEditView`), l’ordinateur cible doit disposer d’une installation de base de Microsoft Internet Explorer 4.0 ou ultérieur.

L’installation de la dernière version de Microsoft Internet Explorer garantit également que l’ordinateur cible dispose des derniers fichiers de contrôle communs. Pour plus d’informations, consultez [Installer et déployer Internet Explorer 11](/internet-explorer/ie11-deploy-guide/install-and-deploy-ie11).

## <a name="see-also"></a>Voir aussi

[Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)