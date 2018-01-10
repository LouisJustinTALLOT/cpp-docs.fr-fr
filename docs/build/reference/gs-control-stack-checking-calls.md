---
title: "-Gs (contrôler les appels de contrôle de pile) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /GS
dev_langs: C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff02465b4e1b1a727a2367c8d5e038f30854ecc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (contrôler les appels de contrôle de pile)
Gère les tests de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>Arguments  
 `size`  
 (Facultatif) Nombre d'octets que les variables locales peuvent occuper avant qu'une sonde de pile soit lancée. Si le **/Gs** option est spécifiée sans un `size` argument, il est identique à la spécification **/Gs0**,  
  
## <a name="remarks"></a>Notes  
 Une sonde de pile est une séquence de code que le compilateur insère dans chaque appel de fonction. Lorsqu'elle est lancée, une sonde de pile pénètre sans heurt dans la mémoire en fonction de l'espace requis pour stocker les variables locales de la fonction.  
  
 Si une fonction requiert plus de `size` octets d'espace de pile pour les variables locales, sa sonde de pile est démarrée. Par défaut, le compilateur génère du code qui lance une sonde de pile quand une fonction requiert plus d'une page d'espace de pile. Cela est équivalent à une option du compilateur **/Gs4096** pour x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]et les plateformes ARM. Cette valeur permet à une application et au gestionnaire de mémoire Windows d’augmenter la quantité de mémoire validée dynamiquement dans la pile du programme au moment de l’exécution.  
  
> [!NOTE]
>  La valeur par défaut **/Gs4096** permet à la pile du programme d’applications pour Windows de croître correctement au moment de l’exécution. Nous vous recommandons de ne pas modifier la valeur par défaut à moins que vous sachiez exactement pourquoi vous devez la changer.  
  
 Certains programmes (par exemple, les pilotes de périphériques virtuels) n'ont pas besoin de ce mécanisme de croissance de pile par défaut. Dans ce cas, les sondes de pile ne sont pas nécessaires et vous pouvez arrêter le compilateur qui les génère en affectant à `size` une valeur supérieure à celle qu'aucune fonction exigera pour le stockage des variables locales. Aucun espace n’est autorisé entre **/Gs** et `size`.  
  
 **/ Gs0** Active les tests de pile pour chaque appel de fonction qui requiert un stockage pour les variables locales. Cela peut avoir un impact négatif sur les performances.  
  
 Vous pouvez activer ou désactiver les tests de pile à l’aide de [check_stack](../../preprocessor/check-stack.md). **/GS** et `check_stack` pragma n’ont aucun effet sur les routines de bibliothèque C standard ; ils affectent uniquement les fonctions que vous compilez.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)