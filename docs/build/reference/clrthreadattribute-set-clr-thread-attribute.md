---
title: -/CLRTHREADATTRIBUTE (attribut de Thread CLR ensemble) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b83c3df380b07f125bad8426b9bf18b013b606c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373421"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Définir l'attribut de thread CLR)
Spécifier explicitement l’attribut de thread pour le point d’entrée de votre programme CLR.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>Paramètres  
 MTA  
 Applique l’attribut MTAThreadAttribute au point d’entrée de votre programme.  
  
 AUCUN  
 Identique à ne pas spécifier /CLRTHREADATTRIBUTE.  Permet de définir la valeur par défaut, attribut de thread du Common Language Runtime (CLR).  
  
 STA  
 Applique l’attribut STAThreadAttribute au point d’entrée de votre programme.  
  
## <a name="remarks"></a>Notes  
 Définition de l’attribut de thread est valide uniquement lors de la création d’un .exe, car il affecte le point d’entrée du thread principal.  
  
 Si vous utilisez le point d’entrée par défaut (main ou wmain, par exemple) spécifiez le modèle de thread en utilisant /CLRTHREADATTRIBUTE ou en plaçant l’attribut de thread (STAThreadAttribute ou MTAThreadAttribute) sur la fonction d’entrée par défaut.  
  
 Si vous utilisez un point d’entrée de celle par défaut, spécifiez le modèle de thread en utilisant /CLRTHREADATTRIBUTE ou en plaçant le threading attribut sur la fonction d’entrée non-par défaut, puis spécifiez le point d’entrée de celle par défaut avec [/ENTRY](../../build/reference/entry-entry-point-symbol.md) .  
  
 Si le modèle de thread spécifié dans le code source ne correspond pas avec le modèle de thread spécifié avec /CLRTHREADATTRIBUTE., l’éditeur de liens ignore /CLRTHREADATTRIBUTE et appliquer le modèle de thread spécifié dans le code source.  
  
 Il sera nécessaire pour pouvoir l’utiliser, par exemple, si votre programme CLR héberge un objet COM qui utilise le modèle de thread unique.  Si votre programme CLR utilise le multithreading, il ne peut pas héberger un objet COM qui utilise le modèle de thread unique.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **avancé** page de propriétés.  
  
5.  Modifier la **attribut de Thread CLR** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)