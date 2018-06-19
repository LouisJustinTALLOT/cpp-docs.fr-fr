---
title: Fichiers affectés par la modification des ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb103ac098c8d73db132cdb67b6ab6902ee3f591
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874354"
---
# <a name="files-affected-by-resource-editing"></a>Fichiers affectés par la modification des ressources
L'environnement Visual Studio fonctionne avec les fichiers indiqués dans le tableau ci-dessous pendant votre session de modification des ressources.  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Resource.h|Fichier d'en-tête généré par l'environnement de développement. Il contient les définitions de symbole.|  
|Filename.aps|Version binaire du fichier de script de ressources actif. Ce fichier est utilisé pour le chargement rapide.<br /><br /> Les éditeurs de ressources ne lisent pas directement les fichiers .rc ou resource.h. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la conservation des commentaires, consultez [, y compris des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).|  
|.rc|Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement.|  
  

  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)