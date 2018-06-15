---
title: Déployer une application Visual C++ dans un dossier local d’application | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a02e585dc2b82c8b8ad675907e4205db6ad7279
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337907"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Procédure pas à pas : déploiement d'une application Visual C++ dans un dossier local de l'application
Décrit comment déployer une application Visual C++ en copiant les fichiers dans son dossier.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Un ordinateur avec Visual Studio installé.  
  
-   Un autre ordinateur sans les bibliothèques Visual C++.  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Pour déployer une application dans un dossier local d’application  
  
1.  Créez et générez une application MFC en suivant les étapes dans [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
2.  Copiez les fichiers de bibliothèque MFC et runtime C (CRT) appropriés, par exemple, pour une plateforme x86 et la prise en charge Unicode, copiez mfc100u.dll et msvcr100.dll à partir de \Program Files\Microsoft Visual Studio 10.0\VC\redist\x86\, puis collez-les dans le dossier \Release\ de votre projet MFC. Pour plus d’informations sur les autres fichiers que vous pouvez avoir à copier, consultez [Détermination des DLL à redistribuer](../ide/determining-which-dlls-to-redistribute.md).  
  
3.  Exécutez l’application MFC sur un deuxième ordinateur sans les bibliothèques Visual C++.  
  
    1.  Copiez le contenu du dossier \Release\ et collez-le dans le dossier d’application sur le deuxième ordinateur.  
  
    2.  Exécutez l’application sur le deuxième ordinateur.  
  
     L’application s’exécute correctement, car les bibliothèques Visual C++ sont disponibles dans le dossier local de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de déploiement](../ide/deployment-examples.md)