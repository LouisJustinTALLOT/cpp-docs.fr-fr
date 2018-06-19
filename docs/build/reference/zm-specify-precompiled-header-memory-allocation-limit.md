---
title: -Zm (spécifier la limite d’Allocation de mémoire en-tête précompilé) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zm
dev_langs:
- C++
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 379d3d6673e673522334d685a47220bcfa2523ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380899"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Spécifier la limite d’allocation mémoire d’en-tête précompilé)
Détermine la quantité de mémoire que le compilateur alloue pour construire des en-têtes précompilés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zmfactor  
```  
  
## <a name="arguments"></a>Arguments  
 `factor`  
 Facteur d’échelle qui détermine la quantité de mémoire que le compilateur utilise pour construire des en-têtes précompilés.  
  
 L'argument `factor` est un pourcentage de la taille par défaut d'une mémoire tampon de travail définie par le compilateur. La valeur par défaut de `factor` est 100 (pour cent), mais vous pouvez spécifier des quantités plus grandes ou plus petites.  
  
## <a name="remarks"></a>Notes  
 Dans les versions antérieures de Visual C++, le compilateur utilisait plusieurs tas discrets, chacun avec une limite finie. Actuellement, le compilateur augmente dynamiquement les tas selon les besoins, jusqu’à ce que la limite de la taille totale des tas soit atteinte. Il requiert ensuite une mémoire tampon de taille fixe uniquement pour construire des en-têtes précompilés. Par conséquent, le **/Zm** option du compilateur est rarement nécessaire.  
  
 Si le compilateur suffisamment d’espace du tas et émet le [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) message d’erreur lorsque vous utilisez la **/Zm** option du compilateur, vous avez réservé trop de mémoire. Envisagez de supprimer le **/Zm** option. Si le compilateur émet le [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) être associé à un message d’erreur [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) message Spécifie le `factor` argument à utiliser lorsque vous recompilez à l’aide de la **/Zm** option du compilateur.  
  
 Le tableau suivant montre comment l'argument `factor` affecte la limite d'allocation de mémoire si vous supposez que la taille de la mémoire tampon de l'en-tête précompilé par défaut est de 75 Mo.  
  
|Valeur de `factor`|Limite d'allocation de mémoire|  
|-----------------------|-----------------------------|  
|10|7.5 MO|  
|100|75 MO|  
|200|150 MO|  
|1000|750 MO|  
|2 000|1 500 MO|  
  
## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Autres moyens de définir la limite d'allocation de mémoire  
  
#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir l'option de compilateur /Zm dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Dans le volet de navigation, sélectionnez **propriétés de Configuration**, **C/C++**, **ligne de commande**.  
  
3.  Entrez le **/Zm** option du compilateur dans le **des Options supplémentaires** boîte.  
  
#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Pour définir l'option de compilateur /Zm par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)