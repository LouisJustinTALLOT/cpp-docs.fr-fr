---
title: -Qvec-report (niveau de rapport du Vectoriseur automatique) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85f9d1c63f41b28982018bbe4507ff6bf87158fb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685851"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Niveau de rapport du vectoriseur automatique)
Active la fonctionnalité de création de rapports du compilateur [Vectoriseur](../../parallel/auto-parallelization-and-auto-vectorization.md) et spécifie le niveau des messages d’information pour la sortie pendant la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>Notes  
 **/ Qvec-report : 1**  
 Génère un message d’information pour les boucles qui sont vectorisées.  
  
 **/ Qvec-report : 2**  
 Génère un message d’information pour les boucles qui sont vectorisées et pour les boucles non vectorisées, ainsi que d’un code de raison.  
  
 Pour plus d’informations sur les codes motif et les messages, consultez [Messages du Vectoriseur et du PARALLÉLISEUR](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Pour définir l’option de compilateur /Qvec-report dans Visual Studio  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2.  Dans le **Pages de propriétés** boîte de dialogue **C/C++**, sélectionnez **ligne de commande**.  
  
3.  Dans le **des Options supplémentaires** , entrez `/Qvec-report:1` ou `/Qvec-report:2`.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Pour définir l’option de compilateur /Qvec-report par programmation  
  
-   Utilisez l'exemple de code fourni dans <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Programmation parallèle en Code natif](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)