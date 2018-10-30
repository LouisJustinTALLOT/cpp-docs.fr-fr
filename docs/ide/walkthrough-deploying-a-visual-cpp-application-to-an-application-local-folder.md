---
title: Déployer une application Visual C++ dans un dossier local d’application | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: 3db193c0537869e4b99bc4c0c94cc79c70f5e827
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060661"
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Procédure pas à pas : déploiement d'une application Visual C++ dans un dossier local de l'application

Décrit comment déployer une application Visual C++ en copiant les fichiers dans son dossier.

## <a name="prerequisites"></a>Prérequis

- Un ordinateur avec Visual Studio installé.

- Un autre ordinateur sans les bibliothèques Visual C++.

### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Pour déployer une application dans un dossier local d’application

1. Créez et générez une application MFC en suivant les étapes dans [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Copiez les fichiers bibliothèque MFC et runtime C (CRT) appropriés à partir du répertoire d’installation de Visual Studio dans le dossier \\VC\\redist\\*version*, puis collez-les dans le dossier \Release\ de votre projet MFC. Pour plus d’informations sur les autres fichiers que vous pouvez avoir à copier, consultez [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md).

1. Exécutez l’application MFC sur un deuxième ordinateur qui ne dispose pas des bibliothèques Visual C++.

   1. Copiez le contenu du dossier \Release\ et collez-le dans le dossier d’application sur le deuxième ordinateur.

   1. Exécutez l’application sur le deuxième ordinateur.

   L’application s’exécute correctement, car les bibliothèques Visual C++ sont disponibles dans le dossier local de l’application.

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](deployment-examples.md)<br/>
