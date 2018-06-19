---
title: -vmm, - VM, - /vmv (représentation à but général) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2f79238c890d43678332203acbe9d935a54102
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379560"
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Représentation à but général)
Utilisé lorsque [/vmb, /vmg (méthode de représentation)](../../build/reference/vmb-vmg-representation-method.md) est sélectionné comme le [méthode de représentation](../../build/reference/vmb-vmg-representation-method.md). Ces options indiquent le modèle d’héritage de la définition de classe d’a pas encore été rencontrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## <a name="remarks"></a>Notes  
 Les options sont décrites dans le tableau suivant.  
  
|Option|Description|  
|------------|-----------------|  
|**/ VMM**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe qui utilise l’héritage multiple.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **multiple_inheritance**.<br /><br /> Cette représentation est supérieure à celle requise pour un héritage simple.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est virtuel, le compilateur génère une erreur.|  
|**/vms**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe pour qu’il n’utilise pas l’héritage ou un héritage simple.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **héritage unique**.<br /><br /> Il s’agit de la plus petite représentation possible d’un pointeur vers un membre d’une classe.<br /><br /> Si le modèle d’héritage d’une définition de classe pour laquelle un pointeur vers un membre est déclaré est de type multiple ou virtuel, le compilateur génère une erreur.|  
|**/vmv**|Spécifie la représentation la plus générale d’un pointeur vers un membre d’une classe qui utilise l’héritage virtuel. Il jamais provoque une erreur et la valeur par défaut.<br /><br /> Correspondants [mot clé d’héritage](../../cpp/inheritance-keywords.md) et l’argument de [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) est **virtual_inheritance**.<br /><br /> Cette option requiert un pointeur plus large et du code supplémentaire pour interpréter le pointeur que les autres options.|  
  
 Lorsque vous spécifiez une de ces options de modèle d’héritage, ce modèle est utilisé pour tous les pointeurs vers des membres de classe, quel que soit leur type d’héritage ou, si le pointeur est déclaré avant ou après la classe. Par conséquent, si vous utilisez toujours des classes d’héritage simple, vous pouvez réduire la taille du code en compilant avec **/VMS**; Cependant, si vous souhaitez utiliser la plupart des cas (au détriment de la représentation de données), compilez avec **/vmv**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/ vmb, /vmg (méthode de représentation)](../../build/reference/vmb-vmg-representation-method.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)