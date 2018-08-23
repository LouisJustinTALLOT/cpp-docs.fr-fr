---
title: LNK1168 d’erreur des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9437b88b67254a63babf5b72379a760d1ab86062
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541750"
---
# <a name="linker-tools-error-lnk1168"></a>Erreur des outils Éditeur de liens LNK1168
impossible d'ouvrir nomfichier en écriture  
  
 L'éditeur de liens ne peut pas écrire dans `filename`. Il est possible que le fichier soit utilisé et que son handle de fichier soit verrouillé par un autre processus. Il est possible également que vous ne disposiez pas de l'autorisation d'accès en écriture pour le fichier, ou pour le répertoire ou le partage réseau dans lequel il est situé. Cette erreur est souvent due à une situation temporaire, par exemple, un verrou détenu par un programme antiviru, processus d’indexation de recherche un fichier ou un retard lors de la libération d’un verrou détenu par le système de génération Visual Studio.  
  
 Pour résoudre ce problème, vérifiez que le handle de fichier de `filename` n'est pas verrouillé, et que vous disposez d'une autorisation d'accès en écriture pour le fichier. S'il s'agit d'un exécutable, vérifiez qu'il n'est pas déjà en cours d'exécution.  
  
 Vous pouvez utiliser les utilitaires Windows SysInternals [gérer](http://technet.microsoft.com/sysinternals/bb896655.aspx) ou [Process Explorer](http://technet.microsoft.com/sysinternals/bb896653) pour déterminer le processus qui possède un fichier de handle de verrou sur `filename`. Vous pouvez également utiliser Process Explorer pour libérer les verrous des handles de fichiers ouverts. Pour plus d'informations sur l'utilisation de ces utilitaires, consultez les fichiers d'aide qui les accompagnent.  
  
 Si le fichier est verrouillé par un antivirus, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'analyse automatique de l'antivirus. Les scanners antivirus sont souvent déclenchés par la création de fichiers dans le système de fichiers. Par ailleurs, ils verrouillent les fichiers pendant l'analyse. Consultez la documentation de votre antivirus pour plus d'informations sur la façon d'exclure des répertoires spécifiques de l'analyse.  
  
 Si le fichier est verrouillé par un service d'indexation de la recherche, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'indexation automatique. Consultez la documentation du service d'indexation pour plus d'informations. Pour modifier la recherche Windows service d’indexation, utilisez **Options d’indexation** dans le Windows **le panneau de configuration**. Pour plus d’informations, consultez [Windows d’améliorer les recherches à l’aide de l’index : Forum aux questions](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7).  
  
 Si votre exécutable ne peut pas être remplacé par le processus de génération, cela signifie qu'il est peut-être verrouillé par l'Explorateur de fichiers. Si le **Application expérience** service a été désactivé, l’Explorateur de fichiers peut conserver un verrou de handle de fichier exécutable pendant une période prolongée. Pour résoudre ce problème, exécutez **services.msc** , puis ouvrez le **propriétés** boîte de dialogue pour le **Application expérience** service. Modifier le **type de démarrage** à partir de **désactivé** à **manuel**.  
  
## <a name="see-also"></a>Voir aussi  
 [Vous pouvez recevoir une « erreur PRJ0008 » ou un message d’erreur « Erreur irrécupérable LNK1168 » lorsque vous essayez de générer une solution ou un projet ActiveX dans Visual C++](http://support.microsoft.com/kb/308358)