---
title: Problèmes de migration de virgule flottante | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb8f7d4835fe50dba2cb7eb6d4e7cb6a54efdbba
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42578281"
---
# <a name="floating-point-migration-issues"></a>Problèmes de migration de virgule flottante  
  
Quand vous mettez à niveau vos projets avec une version plus récente de Visual Studio, vous constaterez peut-être parfois que les résultats de certaines opérations à virgule flottante ont changé. Cela est généralement dû à des modifications de génération de code qui tirent mieux parti du processeur disponible et des correctifs de bogue ou à des modifications apportées aux algorithmes utilisés dans les fonctions mathématiques au sein de la bibliothèque runtime C (CRT). En général, les nouveaux résultats sont corrects dans les limites spécifiées par la norme du langage. Poursuivez votre lecture pour découvrir ce qui a changé et, si c’est important, pour savoir comment obtenir les mêmes résultats que ceux que vos fonctions fournissaient auparavant.  

## <a name="new-math-functions-and-universal-crt-changes"></a>Nouvelles fonctions mathématiques et modifications apportées à la bibliothèque CRT universelle  
  
La plupart des fonctions mathématiques CRT sont présentes dans Visual Studio depuis des années, mais à partir de Visual Studio 2013, toutes les fonctions requises par la norme ISO C99 sont incluses. Ces fonctions sont implémentées pour équilibrer le niveau de performance avec exactitude. Étant donné que la production du résultat correctement arrondi dans chaque cas peut atteindre un coût prohibitif, ces fonctions sont conçues pour produire efficacement une approximation précise du résultat correctement arrondi. Dans la plupart des cas, le résultat produit se situe à +/-1 unité en dernière position (ou *ULP*, Unit in the Last Place), du résultat correctement arrondi, même si parfois, le niveau d’imprécision peut être plus grand. Si vous utilisiez une bibliothèque mathématique différente pour obtenir ces fonctions, des différences d’implémentation peuvent expliquer les modifications dans vos résultats.   
    
Quand les fonctions mathématiques ont été déplacées vers la bibliothèque CRT universelle de Visual Studio 2015, certains nouveaux algorithmes ont été utilisés et plusieurs bogues dans l’implémentation des fonctions qui étaient nouvelles dans Visual Studio 2013 ont été résolus. Ces modifications peuvent entraîner des différences détectables dans les résultats des calculs en virgule flottante qui utilisent ces fonctions. Les fonctions victimes de bogues étaient erf, exp2, remainder, remquo, scalbln et scalbn et leurs variantes de type long double et à virgule flottante.  D’autres changements dans Visual Studio 2015 ont résolu les problèmes liés à la conservation des informations sur l’état d’exception et le mot d’état des opérations à virgule flottante dans les fonctions _clear87, _clearfp, fegetenv, fesetenv et feholdexcept.  
  
## <a name="processor-differences-and-compiler-flags"></a>Différences de processeur et indicateurs de compilateur  
  
De nombreuses fonctions de bibliothèque mathématique à virgule flottante ont des implémentations différentes pour des architectures de processeur différentes. Par exemple, l’implémentation de la bibliothèque CRT x86 32 bits peut être différente de celle de la bibliothèque CRT x64 64 bits. De plus, certaines fonctions peuvent avoir plusieurs implémentations pour une architecture de processeur donnée. L’implémentation la plus efficace est sélectionnée de façon dynamique au moment de l’exécution selon les jeux d’instructions pris en charge par le processeur. Par exemple, dans la bibliothèque CRT x86 32 bits, certaines fonctions ont à la fois une implémentation x87 et une implémentation SSE2. Lors d’une exécution sur un processeur qui prend en charge SSE2, l’implémentation SSE2 plus rapide est utilisée. Lors d’une exécution sur un processeur qui ne prend pas en charge SSE2, l’implémentation x87 plus lente est utilisée. Vous pouvez voir cela pendant la migration de code ancien, car l’option par défaut de l’architecture du compilateur x86 a été remplacée par [/arch:SSE2](../build/reference/arch-x86.md) dans Visual Studio 2012. Étant donné que les différentes implémentations des fonctions de bibliothèque mathématique peuvent utiliser des instructions de processeur différentes et des algorithmes différents pour produire leurs résultats, les fonctions peuvent produire des résultats différents selon les plateformes. Dans la plupart des cas, les résultats se situent à +/-1 ULP (Unit in the Last Place, unité en dernière position) du résultat correctement arrondi, mais les résultats réels peuvent varier selon les processeurs.  
  
Les améliorations apportées à l’exactitude de la génération du code dans différents modes de virgule flottante dans Visual Studio peuvent également affecter les résultats des opérations à virgule flottante quand un ancien code est comparé à un nouveau code, même si vous utilisez les mêmes indicateurs de compilateur. Par exemple, le code généré par Visual Studio 2010 quand [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) (valeur par défaut) ou `/fp:strict` a été spécifié, n’a peut-être pas correctement propagé les valeurs intermédiaires NaN (non numériques) dans les expressions. Ainsi, certaines expressions qui donnaient un résultat numérique dans les compilateurs plus anciens peuvent maintenant produire un résultat NaN correct. Les différences que vous constatez peuvent également être liées au fait que les optimisations de code activées pour `/fp:fast` tirent désormais parti d’un plus grand nombre de fonctionnalités de processeur. Ces optimisations peuvent utiliser moins d’instructions, mais peuvent avoir un impact sur les résultats générés, car certaines opérations intermédiaires auparavant visibles ont été supprimées.  
  
## <a name="how-to-get-identical-results"></a>Comment obtenir des résultats identiques  
  
Dans la plupart des cas, les modifications apportées aux opérations à virgule flottante dans les derniers compilateurs et bibliothèques entraînent un comportement plus rapide et/ou plus correct. Vous pouvez même constater de meilleures performances concernant la consommation du processeur quand des instructions SSE2 remplacent des instructions x87. Cependant, si votre code doit répliquer précisément le comportement à virgule flottante d’un compilateur antérieur, envisagez d’utiliser les fonctionnalités de multiciblage natif de Visual Studio et générez le projet affecté avec l’ancien ensemble d’outils. Pour plus d’informations, consultez [Utiliser le multiciblage natif dans Visual Studio pour générer d’anciens projets](use-native-multi-targeting.md).  
  
## <a name="see-also"></a>Voir aussi  
  
[Mise à niveau de projets à partir de versions antérieures de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Vue d’ensemble des problèmes de mise à niveau potentiels (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md)  