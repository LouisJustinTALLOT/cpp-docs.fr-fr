---
title: Erreur LNK2001 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78dc0c0a3a030ecb88d7138484e2c64e145f69ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2001"></a>Erreur des outils Éditeur de liens LNK2001
symbole externe non résolu «*symbole*»  
  
Le code compilé effectue une référence ou un appel à *symbole*, mais ce symbole n’est pas défini dans une des bibliothèques ou des fichiers d’objet spécifiés à l’éditeur de liens.  
  
Ce message d’erreur est suivi d’une erreur irrécupérable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Vous devez corriger les erreurs de tous les LNK2001 et l’erreur LNK2019 pour résoudre l’erreur LNK1120.  
  
## <a name="possible-causes"></a>Causes possibles  
  
Il existe plusieurs façons d’obtenir cette erreur, mais tous les impliquent une référence à une fonction ou une variable qui n’est pas l’éditeur de liens *résoudre*, ou de trouver une définition pour. Le compilateur peut identifier quand un symbole n’est pas *déclaré*, mais pas lorsqu’il n’est pas *défini*, car la définition peut être dans un autre fichier source ou la bibliothèque. Si un symbole est référencé mais jamais défini, l’éditeur de liens génère une erreur.  
  
### <a name="coding-issues"></a>Problèmes de codage  
  
Cette erreur peut être provoquée par la casse ne correspondent pas dans votre code source ou la définition de module (.def) fichier. Par exemple, si vous le nommez une variable `var1` dans un C++ fichier source et essayez d’y accéder en tant que `VAR1` dans un autre, cette erreur est générée. Pour résoudre ce problème, utilisez toujours correctement orthographié et casse des noms.  
  
Cette erreur peut être provoquée dans un projet qui utilise [des fonctions inline](../../error-messages/tool-errors/function-inlining-problems.md) si vous définissez les fonctions dans un fichier source, plutôt que dans un fichier d’en-tête. Fonctions inline ne sont pas visibles en dehors du fichier source qui les définit. Pour résoudre ce problème, définissez les fonctions inline dans les en-têtes dans lesquels ils sont déclarés.  
  
Cette erreur peut être provoquée si vous appelez une fonction C à partir d’un programme C++ sans utiliser un `extern "C"` déclaration de la fonction C. Le compilateur utilise les conventions d’affectation de noms autre symbole interne pour le code C et C++, et il est le nom du symbole interne qui recherche l’éditeur de liens lors de la résolution des symboles. Pour résoudre ce problème, utilisez un `extern "C"` wrapper autour de toutes les déclarations de fonctions C utilisées dans votre code C++, ce qui permet au compilateur d’utiliser la convention d’affectation de noms interne de C pour ces symboles. Options du compilateur [/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) et [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) le compilateur de compiler les fichiers sous forme C++ ou C, respectivement, quelle que soit l’extension de nom de fichier. Ces options peuvent causer des noms de fonction interne différentes de ce que vous attendez.  
  
Cette erreur peut résulter d’une tentative de référencer des fonctions ou des données qui n’ont pas une liaison externe. En C++, les fonctions inline et `const` données ont une liaison interne sauf spécification explicite `extern`. Pour résoudre ce problème, utilisez explicite `extern` déclarations sur les symboles référencé en dehors du fichier source de définition.  
  
Cette erreur peut être provoquée par une [corps de fonction ou variable manquant](../../error-messages/tool-errors/missing-function-body-or-variable.md) définition. Cette erreur est courant lorsque vous déclarez, mais que vous ne définissez pas, variables, fonctions ou des classes dans votre code. Le compilateur a uniquement besoin d’un prototype de fonction ou `extern` déclaration de variable pour générer un fichier d’objet sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à la fonction ou une référence à la variable, car il n’existe aucun espace de code ou de variable (fonction) réservé. Pour résoudre ce problème, assurez-vous que chaque fonction référencée et la variable sont entièrement défini dans un fichier source ou de la bibliothèque inclus dans votre lien.  
  
Cette erreur peut être provoquée par un appel de fonction qui utilise les types de retour et de paramètres ou les conventions d’appel qui ne correspondent pas à celles figurant dans la définition de fonction. Dans les fichiers d’objet C++, [décoration de nom](../../error-messages/tool-errors/name-decoration.md) incorpore la convention d’appel, portée de classe ou espace de noms et types de retour et de paramètres d’une fonction dans le nom décoré final de la fonction, qui est utilisé comme symbole à correspondent lorsque des appels à la fonction à partir d’autres fichiers d’objets sont résolus. Pour résoudre ce problème, assurez-vous que la déclaration, la définition et les appels à la fonction de tous les utilisent les mêmes étendues, les types et les conventions d’appel.  
  
Cette erreur peut être provoquée dans du code C++, lorsque vous incluez un prototype de fonction dans une définition de classe, mais ne parviennent pas à [incluent l’implémentation](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la fonction, puis l’appeler. Pour résoudre ce problème, veillez à fournir une définition pour tous les appelée déclarés d’une classe.  
  
Cette erreur peut résulter d’une tentative d’appel d’une fonction virtuelle pure à partir de la classe de base abstraite. Il n’y a aucune implémentation de la classe de base pour une fonction virtuelle pure. Pour résoudre ce problème, assurez-vous que toutes les fonctions virtuelles sont implémentées.  
  
Cette erreur peut être provoquée par une tentative d’utilisation d’une variable déclarée dans une fonction ([une variable locale](../../error-messages/tool-errors/automatic-function-scope-variables.md)) en dehors de la portée de cette fonction. Pour résoudre ce problème, supprimez la référence à la variable qui n’est pas dans la portée, ou déplacez la variable à une étendue plus élevée.  
  
Cette erreur peut se produire lorsque vous générez une version d’un projet ATL, génère un message que le code de démarrage du CRT est requis. Pour résoudre ce problème, effectuez l’une des opérations suivantes,  
  
-   Supprimer `_ATL_MIN_CRT` dans la liste du préprocesseur définit pour autoriser le code de démarrage du CRT à inclure. Consultez [général, Page de propriétés (projet)](../../ide/general-property-page-project.md) pour plus d’informations.  
  
-   Si possible, supprimez les appels aux fonctions CRT qui nécessitent le code de démarrage du CRT. Utilisez plutôt leurs équivalents Win32. Par exemple, utilisez `lstrcmp` au lieu de `strcmp`. Les fonctions connues qui requièrent le code de démarrage du CRT sont des fonctions à virgule flottante de chaîne.  
  
### <a name="compilation-and-link-issues"></a>Problèmes de compilation et liaison  
  
Cette erreur peut se produire lorsque le projet est manque-t-il une référence à une bibliothèque (. LIB) ou un objet (. Fichier OBJ). Pour résoudre ce problème, ajoutez une référence à la bibliothèque requise ou le fichier objet à votre projet. Pour plus d’informations, consultez [fichiers .lib en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).  
  
Cette erreur peut se produire si vous utilisez la [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) ou [/Zl](../../build/reference/zl-omit-default-library-name.md) options. Lorsque vous spécifiez ces options, les bibliothèques qui contiennent le code requis ne sont pas liés dans le projet, sauf si vous les avez incluses explicitement. Pour résoudre ce problème, inclure explicitement toutes les bibliothèques que vous utilisez sur la ligne de commande. Si vous voyez plusieurs noms de fonctions CRT ou de la bibliothèque Standard manquants lorsque vous utilisez ces options, vous devez explicitement incluent les fichiers CRT et des DLL de la bibliothèque Standard ou des bibliothèques dans le lien.  

Si vous compilez à l’aide de la **/CLR** option, il peut y avoir une référence manquante pour .cctor. Pour résoudre ce problème, consultez [l’initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md) pour plus d’informations.  
  
Cette erreur peut se produire si vous la liaison avec les bibliothèques en mode de mise en production lors de la création d’une version debug d’une application. De même, si vous utilisez les options **/MTd** ou **/MDd** ou définissez `_DEBUG` et ensuite lier aux bibliothèques de mise en production, vous devriez constater de nombreux éventuels externes non résolus, entre autres problèmes. Liaison d’une génération en mode de mise en production avec les bibliothèques de débogage provoque également des problèmes similaires. Pour résoudre ce problème, assurez-vous que vous utilisez les bibliothèques de débogage dans les versions de débogage et génère des bibliothèques de vente au détail dans votre commerce de détail.  
  
Cette erreur peut se produire si votre code fait référence à un symbole d’une version d’une bibliothèque, mais que vous fournissez une version différente de la bibliothèque pour l’éditeur de liens. En règle générale, vous ne pouvez pas mélanger des fichiers objets ou bibliothèques qui sont générés pour les différentes versions du compilateur. Les bibliothèques qui sont fournis dans une nouvelle version peuvent contenir des symboles qui ne figure pas dans les bibliothèques incluses dans les versions précédentes et vice versa. Pour résoudre ce problème, générez tous les fichiers objets et les bibliothèques avec la même version du compilateur avant de les relier.  
  
-  Les outils &#124; Options &#124; projets &#124; boîte de dialogue répertoires VC ++, dans la sélection de fichiers de bibliothèque, vous permet de modifier l’ordre de recherche de bibliothèque. Le dossier de l’éditeur de liens dans la boîte de dialogue Pages de propriétés du projet peut également contenir des chemins d’accès qui peuvent être obsolètes.  
  
-  Ce problème peut apparaître lorsqu’un nouveau SDK est installé (par exemple pour un emplacement différent), et l’ordre de recherche n’est pas mis à jour pour pointer vers le nouvel emplacement. En règle générale, vous devez placer le chemin d’accès au nouveau SDK include et lib répertoires devant l’emplacement de Visual C++ par défaut. Également, un projet contenant des chemins incorporés peut pointer vers d’anciens chemins qui sont valides, mais il est plus à jour des nouvelles fonctionnalités ajoutées par la nouvelle version qui est installée dans un autre emplacement.  
  
-   Si vous générez sur la ligne de commande et que vous avez créé vos propres variables d’environnement, vérifiez que les chemins d’accès aux outils, bibliothèques et fichiers d’en-tête dirigé vers une version cohérente. Pour plus d’informations, consultez [définir le chemin d’accès et les Variables d’environnement pour les générations de ligne de commande](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
  
Il n’existe actuellement aucune norme [d’affectation de noms C++](../../error-messages/tool-errors/name-decoration.md) entre les éditeurs de compilateurs ou même entre différentes versions d’un compilateur. Par conséquent, la liaison de fichiers objets compilés avec d’autres compilateurs ne peut pas produire le même schéma d’affectation de noms et donc causer l’erreur LNK2001.  
  
[Options de compilation de mélange non inline et inline](../../error-messages/tool-errors/function-inlining-problems.md) sur des modules différents peut causer LNK2001. Si une bibliothèque C++ est créée avec la fonctionnalité inline activée (**/Ob1** ou **/Ob2**), mais le fichier d’en-tête correspondant décrivant les fonctions a désactivé cette fonctionnalité (aucun `inline` mot clé), cette erreur se produit. Pour résoudre ce problème, définissez les fonctions `inline` dans le fichier d’en-tête inclus dans les autres fichiers sources.  
  
Si vous utilisez la `#pragma inline_depth` Assurez-vous de directive de compilateur que vous avez un [valeur égale ou supérieure à 2](../../error-messages/tool-errors/function-inlining-problems.md)et assurez-vous que vous utilisez également le [/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/Ob2](../../build/reference/ob-inline-function-expansion.md) option du compilateur.  
  
Cette erreur peut se produire si vous omettez le lien option /NOENTRY lorsque vous créez une DLL de ressource uniquement. Pour résoudre ce problème, ajoutez l’option /NOENTRY à la commande de lien.  
  
Cette erreur peut se produire si vous utilisez /SUBSYSTEM incorrect ou les paramètres /ENTRY dans votre projet. Par exemple, si vous écrivez une application console et que vous spécifiez/SUBSYSTEM : Windows, une erreur externe non résolue est générée pour `WinMain`. Pour résoudre ce problème, assurez-vous que vous faire correspondre les options pour le type de projet. Pour plus d’informations sur ces options et les points d’entrée, consultez le [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) et [/ENTRY](../../build/reference/entry-entry-point-symbol.md) les options de l’éditeur de liens.  
  
### <a name="exported-symbol-issues"></a>Problèmes de symbole exporté  
  
Cette erreur se produit lorsqu’une exportation répertoriée dans un fichier .def est introuvable. Cela peut être, car il n’existe pas, est mal orthographié ou utilise des noms décorés. Un fichier .def n’accepte pas les noms décorés. Pour résoudre ce problème, supprimez les exportations inutiles et utilisez `extern "C"` déclarations pour les symboles exportés.  
  
## <a name="what-is-an-unresolved-external-symbol"></a>Qu’est un symbole externe non résolu ?  
  
A *symbole* est le nom d’une fonction ou une variable globale utilisée en interne par un fichier objet compilé ou la bibliothèque. Un symbole est *défini* dans le fichier objet où le stockage est alloué pour une variable globale ou pour une fonction, dans lequel est placé le code compilé pour le corps de la fonction. Un *symbole externe* est un symbole de *référencé*, autrement dit, utilisé ou appelé dans un fichier objet, mais définis dans un fichier de bibliothèque ou un objet différent. Un *exporté symbole* est celui qui est accessible publiquement par le fichier objet ou la bibliothèque qui le définit. L’éditeur de liens doit *résoudre*, ou recherchez la définition correspondante pour chaque symbole externe référencé par un fichier objet lorsqu’il est lié à une application ou une DLL. L’éditeur de liens génère une erreur lorsqu’il ne peut pas résoudre un symbole externe en recherchant un symbole exporté correspondant dans un des fichiers liés.    
  
## <a name="use-the-decorated-name-to-find-the-error"></a>Utiliser le nom décoré pour rechercher l’erreur
  
L’utilisation du compilateur et l’éditeur de liens C++ [décoration de nom](../../error-messages/tool-errors/name-decoration.md), également appelé *substantypage*, pour encoder les informations supplémentaires sur le type d’une variable ou le type de retour, les types de paramètre, étendue et l’appel convention d’une fonction dans le nom du symbole. Ce nom décoré est le nom du symbole l’éditeur de liens recherche pour résoudre les symboles externes.  
  
Étant donné que les informations supplémentaires deviennent une partie du nom du symbole, une erreur de lien peut entraîner si la déclaration d’une variable ou une fonction ne correspond pas exactement à la définition de la fonction ou une variable. Cela peut se produire même si le même fichier d’en-tête est utilisé dans le code appelant et le code de définition si les indicateurs de compilateur différents sont utilisés lors de la compilation des fichiers sources. Par exemple, vous pouvez obtenir cette erreur si votre code est compilé pour utiliser le `__vectorcall` convention d’appel, mais vous connecter à une bibliothèque qui attend que les clients à appeler à l’aide de la valeur par défaut `__cdecl` ou `__fastcall` convention d’appel. Dans ce cas, les symboles ne correspondent pas, car les conventions d’appel sont différentes   
  
Pour vous aider à trouver la cause de ce type d’erreur, le message d’erreur de l’éditeur de liens vous montre les deux le « nom convivial, « le nom utilisé dans le code source et le nom décoré (entre parenthèses) pour le symbole externe non résolu. Vous n’avez pas besoin de savoir comment traduire le nom décoré pour être en mesure de comparer avec les autres noms décorés. Vous pouvez utiliser les outils de ligne de commande qui sont inclus avec le compilateur pour comparer le nom de symbole attendu et le nom de symbole réel :  

-   Le [/EXPORTE](../../build/reference/dash-exports.md) et [/symboles](../../build/reference/symbols.md) options de l’outil de ligne de commande DUMPBIN peuvent vous aider à identifier les symboles qui sont définis dans vos fichiers .dll et objets ou bibliothèques. Cela permet de vérifier que le décorés exportés noms décorés l’éditeur de liens recherche les noms correspondent à.  
  
Dans certains cas, l’éditeur de liens peut signaler uniquement le nom décoré pour un symbole. Vous pouvez utiliser l’outil de ligne de commande UNDNAME pour obtenir la forme non décorée d’un nom décoré.  
  
## <a name="additional-resources"></a>Ressources supplémentaires  
  
Pour plus d’informations sur les causes et solutions pour LNK2001, consultez la question Stack Overflow [qu’est une erreur de symbole externe non défini référence/non résolu et comment la corriger ?](http://stackoverflow.com/q/12573816/2002113).  

