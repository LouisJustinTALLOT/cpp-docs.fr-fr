---
title: -GR (activer les informations de Type au moment de l’exécution) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs:
- C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 993465bd1666e624777e52cb1c3d3a54545589dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Activer les informations de type au moment de l'exécution)
Ajoute du code pour vérifier les types d’objet en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GR[-]  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque **/GR** est activé, le compilateur définit le `_CPPRTTI` macro de préprocesseur. Par défaut, **/GR** sur. **/GR-** désactive les informations de type au moment de l’exécution.  
  
 Utilisez **/GR** si le compilateur ne peut pas résoudre statiquement de type d’objet dans votre code. Vous devez généralement le **/GR** option lorsque votre code utilise [opérateur dynamic_cast](../../cpp/dynamic-cast-operator.md) ou [typeid](../../cpp/typeid-operator.md). Toutefois, **/GR** augmente la taille des sections .rdata de votre image. Si votre code n’utilise pas **dynamic_cast** ou **typeid**, **/GR-** peut produire une image plus petite.  
  
 Pour plus d’informations sur la vérification de type au moment de l’exécution, consultez [Run-Time Type Information](../../cpp/run-time-type-information.md) dans les *référence du langage C++*.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **langage** page de propriétés.  
  
4.  Modifier la **activer les informations sur le Type d’exécution** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)