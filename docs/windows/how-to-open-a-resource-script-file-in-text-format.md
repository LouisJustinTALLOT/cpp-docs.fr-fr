---
title: 'Comment : ouvrir un fichier de Script de ressources au Format texte | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 345171742f979e488c6a4bb48cf1b57e4bb2f164
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018108"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Comment : ouvrir un fichier de script de ressources au format texte
Parfois, vous souhaitez afficher le contenu du fichier de script (.rc) de ressources de votre projet sans ouvrir une ressource, par exemple une boîte de dialogue, dans son éditeur de ressources spécifique. Par exemple, vous souhaitez rechercher une chaîne dans toutes les boîtes de dialogue du fichier de ressources sans avoir à ouvrir chacune d'elles séparément.  
  
> [!NOTE]
>  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
 Vous pouvez facilement ouvrir le fichier de ressources au format texte pour afficher toutes les ressources qu’il contient et effectuer des opérations globales prises en charge par le [éditeur de texte](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Les éditeurs de ressources ne lisent pas directement .rc ou `resource.h` fichiers. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md).  
  
### <a name="to-open-a-resource-script-file-as-text"></a>Pour ouvrir un fichier de script de ressources au format texte  
  
1.  À partir de la **fichier** menu Choisissez **Open**, puis cliquez sur **fichier.**  
  
2.  Dans le **ouvrir un fichier** boîte de dialogue, accédez au fichier de script de ressources à afficher au format texte.  
  
3.  Mettez en surbrillance le fichier, puis cliquez sur la flèche déroulante du **Open** bouton (situé à droite du bouton).  
  
4.  Choisissez **ouvrir avec** dans le menu déroulant.  
  
5.  Dans le **ouvrir avec** boîte de dialogue, cliquez sur **éditeur de Code Source (texte)**.  
  
6.  À partir de la **ouvrir en tant que** liste déroulante, sélectionnez **texte**.  
  
     La ressource s’ouvre dans le **Code Source** éditeur.  
  
 \- ou -  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le fichier .rc.  
  
2.  Dans le menu contextuel, choisissez **ouvrir avec...** , puis sélectionnez **éditeur de Code Source (texte)**.  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)