---
title: "-sdl (activer les contrôles de sécurité supplémentaires) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
dev_langs:
- C++
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbcb74272fa7cae3dd0c641bd6371c8f0f9c204
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (activer des contrôles de sécurité supplémentaires)
Ajoute les vérifications SDL (Security Development Lifecycle) recommandées. Ces vérifications incluent des avertissements supplémentaires relatifs à la sécurité en tant qu’erreurs, ainsi que des fonctionnalités de génération de code sécurisé supplémentaires.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/sdl[-]  
```  
  
## <a name="remarks"></a>Notes  
 **/SDL** Active un sur-ensemble des vérifications de sécurité de base fournie par [/GS](../../build/reference/gs-buffer-security-check.md) et remplacements **/GS-**. Par défaut, **/sdl** est désactivée. **/SDL-** désactive les vérifications de sécurité supplémentaires.  
  
## <a name="compile-time-checks"></a>Vérifications au moment de la compilation  
 **/SDL** Active les avertissements comme des erreurs :  
  
|Avertissement activé par /sdl|Commutateur de ligne de commande équivalent|Description|  
|------------------------------|-------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Un opérateur moins unaire a été appliqué à un type non signé, ce qui génère un résultat non signé.|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Une constante intégrale négative a été convertie en type non signé, générant éventuellement un résultat sans signification.|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Utilisation de `continue`, `break` ou `goto` mots clés dans un `__finally` / `finally` bloc a un comportement indéfini lors d’un arrêt anormal.|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Le code d'initialisation d'une variable ne sera pas exécuté.|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Utilisation d'une variable locale non initialisée.|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Utilisation d'une variable de pointeur locale potentiellement non initialisée.|  
|[ERREUR C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Dépassement de mémoire tampon quand des fonctions CRT (Runtime C) spécifiques sont utilisées.|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Utilisation d’une fonction marquée avec le pragma [déconseillée](../../preprocessor/deprecated-c-cpp.md).|  
|[ERREUR C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Utilisation d’une fonction marquée en tant que [déconseillée](../../cpp/deprecated-cpp.md).|  
  
## <a name="runtime-checks"></a>Vérifications au moment de l'exécution  
 Lorsque **/sdl** est activé, le compilateur génère du code pour effectuer ces vérifications au moment de l’exécution :  
  
-   Active le mode strict de **/GS** détection de dépassement de mémoire tampon d’exécution, équivalente à la compilation avec `#pragma strict_gs_check(push, on)`.  
  
-   Effectue un assainissement de pointeur limité. Dans les expressions qui n'impliquent pas de déréférencements et dans les types qui n'ont aucun destructeur défini par l'utilisateur, les références de pointeur sont définies sur une adresse non valide après un appel à `delete`. Cela contribue à empêcher la réutilisation de références périmées de pointeur.  
  
-   Effectue l'initialisation des membres de classe. Initialise automatiquement tous les membres de classe à zéro lors de l'instanciation d'objet (avant l'exécution du constructeur). Cela contribue à éviter l'utilisation de données non initialisées associées aux membres de classe que le constructeur n'initialise pas explicitement.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [avertissements, /sdl et amélioration de la détection des variable non initialisées](http://go.microsoft.com/fwlink/p/?LinkId=331012).  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sur le **général** page, sélectionnez l’option à partir de la **vérifications SDL** liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)