---
title: -LN (créer un Module MSIL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 918b3857c2e6f26a7f2e11614a00049e9b615ea8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375309"
---
# <a name="ln-create-msil-module"></a>/LN (Créer le module MSIL)
Indique qu'un manifeste d'assembly ne doit pas être inséré dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/LN  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, **/LN** n’est pas activé (un manifeste d’assembly est inséré dans le fichier de sortie).  
  
 Lors de la **/LN** est utilisé, parmi les [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) options doivent également être utilisées.  
  
 Un programme managé qui ne possède pas de métadonnées d’assembly dans le manifeste est appelé un module. Si vous compilez avec [/c (compiler sans liaison)](../../build/reference/c-compile-without-linking.md) et **/LN**, spécifiez [/NOASSEMBLY (créer un Module MSIL)](../../build/reference/noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer le fichier de sortie.  
  
 Voulez-vous créer des modules si vous souhaitez effectuer une approche basée sur le composant pour générer des assemblys.  Autrement dit, vous pouvez créer des types et les compiler dans des modules.  Ensuite, vous pouvez générer un assembly à partir d’un ou plusieurs modules.  Pour plus d’informations sur la création d’assemblys à partir de modules, consultez [fichiers .netmodule en tant qu’entrée de l’éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md) ou [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).  
  
 L’extension de fichier par défaut pour un module est .netmodule.  
  
 Dans [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] les versions antérieures à Visual C++ 2005, un module a été créé avec **/CLR : noAssembly**.  
  
 L’éditeur de liens Visual C++ accepte les fichiers .netmodule en tant qu’entrée et le fichier de sortie produit par l’éditeur de liens sera un assembly ou un fichier .netmodule sans dépendance d’exécution sur un des fichiers .netmodule entrés dans l’éditeur de liens.  Pour plus d’informations, consultez [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
-   Spécifiez [/NOASSEMBLY (créer un Module MSIL)](../../build/reference/noassembly-create-a-msil-module.md) dans la phase de l’éditeur de liens pour créer le fichier de sortie.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Cette option du compilateur ne peut pas être modifiée par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)