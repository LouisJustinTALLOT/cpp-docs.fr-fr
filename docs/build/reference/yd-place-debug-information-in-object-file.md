---
title: -Yd (placer les informations de débogage dans un fichier objet) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yd
dev_langs:
- C++
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b03b0faf975caba8c5a287c88afcdf53f7a71f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378231"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Placer les informations de débogage dans un fichier objet)
Espace complète les informations de débogage dans tous les fichiers objets créés à partir d’un fichier d’en-tête précompilé (.pch) lorsqu’il est utilisé avec le [/Yc](../../build/reference/yc-create-precompiled-header-file.md) et [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) options. Obsolète.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>Notes  
 **/Yd** est déconseillé ; [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] utiliser de prend désormais en charge plusieurs objets qui écrivent dans un fichier .pdb unique, **/Zi** à la place. Pour obtenir la liste des options du compilateur déconseillées, consultez **déconseillées et supprimées des Options du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 Sauf si vous devez distribuer une bibliothèque contenant débogage des informations, utilisez le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option plutôt que **/Z7** et **/Yd**.  
  
 Le stockage des informations de débogage complètes dans chaque fichier .obj est nécessaire uniquement pour la distribution de bibliothèques qui contiennent des informations de débogage. Il ralentit la compilation et nécessite un espace disque considérable. Lorsque **/Yc** et **/Z7** sont utilisées sans **/Yd**, le compilateur stocke les informations de débogage communes dans le premier fichier .obj créé à partir du fichier .pch. Le compilateur n’insère pas ces informations dans des fichiers .obj créés par la suite à partir du fichier .pch ; Il insère les renvois aux informations. Quel que soit le nombre de fichiers .obj utilisent le fichier .pch, un seul fichier .obj contient les informations de débogage courantes.  
  
 Bien que ce comportement se traduit par défaut dans les délais de génération plus rapidement et réduit les besoins en espace disque, il n’est pas souhaitable si une petite modification nécessite la reconstruction du fichier .obj contenant les informations de débogage communes. Dans ce cas, le compilateur doit régénérer tous les fichiers .obj qui contient des références croisées au fichier .obj d’origine. En outre, si un fichier .pch commun est utilisé par différents projets, il est difficile d’envers les références croisées à un seul fichier .obj.  
  
 Pour plus d’informations sur les en-têtes précompilés, consultez :  
  
-   [/Y (En-têtes précompilés)](../../build/reference/y-precompiled-headers.md)  
  
-   [Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="examples"></a>Exemples  
 Supposez que vous avez deux fichiers de base, F.cpp et G.cpp, chacun contenant ces **#include** instructions :  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 La commande suivante crée l’en-tête précompilé du fichier ETC.pch et le fichier objet F.obj :  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 Le fichier objet F.obj inclut le type et les informations de symboles pour WINDOWS.h et ETC.h (et tous les autres fichiers d’en-tête qu’ils incluent). Vous pouvez maintenant utiliser l’en-tête précompilé ETC.pch pour compiler le fichier source G.cpp :  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 Le fichier objet G.obj n’inclut pas les informations de débogage pour l’en-tête précompilé, mais uniquement des références à ces informations dans le fichier F.obj. Notez que vous devez lier avec le fichier F.obj.  
  
 Si votre en-tête précompilé n’a pas été compilée avec **/Z7**, vous pouvez l’utiliser dans des compilations ultérieures à l’aide de **/Z7**. Toutefois, les informations de débogage sont placées dans le fichier objet en cours, et les symboles locaux pour les fonctions et les types définis dans l’en-tête précompilé ne sont pas disponibles pour le débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)