---
title: Erreur des outils Éditeur de liens LNK2001
ms.date: 12/19/2019
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: b6d1e53d8f057ddc93e2dfde65cb951d247dfcc0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302131"
---
# <a name="linker-tools-error-lnk2001"></a>Erreur des outils Éditeur de liens LNK2001

> symbole externe non résolu "*symbol*"

Le code compilé fait une référence ou un appel au *symbole*. Le symbole n’est pas défini dans les bibliothèques ou les fichiers objets recherchés par l’éditeur de liens.

Ce message d’erreur est suivi de l’erreur irrécupérable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Pour corriger l’erreur LNK1120, corrigez d’abord toutes les erreurs LNK2001 et LNK2019.

Il existe plusieurs façons d’accéder à des erreurs LNK2001. Tous impliquent une *référence* à une fonction ou une variable que l’éditeur de liens ne peut pas *résoudre*, ou trouver une définition pour. Le compilateur peut identifier le moment où votre code ne *déclare* pas de symbole, mais pas lorsqu’il n’en *définit* pas un. Cela est dû au fait que la définition peut se trouver dans un fichier source ou une bibliothèque différent (e). Si votre code fait référence à un symbole, mais qu’il n’est jamais défini, l’éditeur de liens génère une erreur.

## <a name="what-is-an-unresolved-external-symbol"></a>Qu’est-ce qu’un symbole externe non résolu ?

Un *symbole* est le nom interne d’une fonction ou d’une variable globale. Il s’agit de la forme du nom utilisé ou défini dans un fichier objet ou une bibliothèque compilé (e). Une variable globale est définie dans le fichier objet où le stockage est alloué. Une fonction est définie dans le fichier objet où le code compilé pour le corps de la fonction est placé. Un *symbole externe* est référencé dans un fichier objet, mais il est défini dans une bibliothèque ou un fichier objet différent. Un *symbole exporté* est un symbole qui est mis à la disposition du public par le fichier objet ou la bibliothèque qui le définit.

Pour créer une application ou une DLL, chaque symbole utilisé doit avoir une définition. L’éditeur de liens doit *résoudre*ou trouver la définition correspondante pour, chaque symbole externe référencé par chaque fichier objet. L’éditeur de liens génère une erreur lorsqu’il ne peut pas résoudre un symbole externe. Cela signifie que l’éditeur de liens n’a pas pu trouver une définition de symbole exportée correspondante dans l’un des fichiers liés.

## <a name="compilation-and-link-issues"></a>Problèmes de compilation et de liaison

Cette erreur peut se produire :

- Lorsqu’il manque une référence à une bibliothèque dans le projet (. LIB) ou d’objet (. Fichier OBJ). Pour résoudre ce problème, ajoutez une référence à la bibliothèque ou au fichier objet requis dans votre projet. Pour plus d’informations, consultez [fichiers lib en tant qu’entrée dans l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

- Lorsque le projet a une référence à une bibliothèque (. LIB) ou d’objet (. OBJ) qui, à son tour, requiert des symboles d’une autre bibliothèque. Cela peut se produire même si vous n’appelez pas les fonctions qui provoquent la dépendance. Pour résoudre ce problème, ajoutez une référence à l’autre bibliothèque dans votre projet. Pour plus d’informations, consultez [comprendre le modèle classique pour la liaison : prise de symboles pour la définition](https://devblogs.microsoft.com/oldnewthing/20130108-00/?p=5623).

- Si vous utilisez les options [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) ou [/zl](../../build/reference/zl-omit-default-library-name.md) . Lorsque vous spécifiez ces options, les bibliothèques qui contiennent du code requis ne sont pas liées au projet, sauf si vous les incluez explicitement. Pour résoudre ce problème, incluez explicitement toutes les bibliothèques que vous utilisez sur la ligne de commande de liaison. Si vous voyez de nombreux noms de fonction CRT ou de bibliothèque standard manquants lorsque vous utilisez ces options, incluez explicitement les dll de bibliothèque CRT et standard ou les fichiers de bibliothèque dans le lien.

- Si vous compilez à l’aide de l’option **/CLR** . Il peut y avoir une référence manquante à `.cctor`. Pour plus d’informations sur la résolution de ce problème, consultez [initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).

- Si vous créez un lien vers les bibliothèques en mode release lors de la génération d’une version Debug d’une application. De même, si vous utilisez les options **/MTD** ou **/MDD** ou que vous définissez `_DEBUG` puis que vous liez les bibliothèques de version, vous devez vous attendre à de nombreux problèmes externes non résolus, entre autres. La liaison d’une build en mode mise en sortie avec les bibliothèques de débogage entraîne également des problèmes similaires. Pour résoudre ce problème, veillez à utiliser les bibliothèques de débogage dans vos versions Debug et les bibliothèques de vente au détail dans vos builds de vente au détail.

- Si votre code fait référence à un symbole d’une version de bibliothèque, mais que vous liez une autre version de la bibliothèque. En règle générale, vous ne pouvez pas mélanger des fichiers objets ou des bibliothèques qui sont générés pour différentes versions du compilateur. Les bibliothèques fournies dans une version peuvent contenir des symboles introuvables dans les bibliothèques incluses avec d’autres versions. Pour résoudre ce problème, générez tous les fichiers objets et les bibliothèques avec la même version du compilateur avant de les lier ensemble. Pour plus d’informations, consultez [ C++ compatibilité binaire 2015-2019](../../porting/binary-compat-2015-2017.md).

- Si les chemins d’accès à la bibliothèque sont obsolètes. La boîte de dialogue **outils > Options > projets > Répertoires VC + +** , sous la sélection **fichiers de bibliothèque** , vous permet de modifier l’ordre de recherche de la bibliothèque. Le dossier de l’éditeur de liens dans la boîte de dialogue pages de propriétés du projet peut également contenir des chemins qui peuvent être obsolètes.

- Lors de l’installation d’un nouveau SDK Windows (peut-être à un autre emplacement). L’ordre de recherche de la bibliothèque doit être mis à jour pour pointer vers le nouvel emplacement. Normalement, vous devez placer le chemin vers le nouveau kit de développement logiciel (SDK) include et C++ les répertoires lib devant l’emplacement du visuel par défaut. En outre, un projet contenant des chemins d’accès incorporés peut toujours pointer vers des anciens chemins d’accès qui sont valides, mais obsolètes. Mettez à jour les chemins d’accès pour les nouvelles fonctionnalités ajoutées par la nouvelle version installée à un autre emplacement.

- Si vous générez à partir de la ligne de commande, et que vous avez créé vos propres variables d’environnement. Vérifiez que les chemins d’accès aux outils, bibliothèques et fichiers d’en-tête sont compatibles avec une version cohérente. Pour plus d’informations, consultez [définir le chemin d’accès et les variables d’environnement pour les générations à partir de la ligne de commande](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

## <a name="coding-issues"></a>Problèmes de codage

Cette erreur peut avoir les explications suivantes :

- La casse ne correspond pas dans le code source ou le fichier de définition de module (. def). Par exemple, si vous nommez une variable `var1` dans C++ un fichier source et essayez d’y accéder en tant que `VAR1` dans une autre, cette erreur est générée. Pour résoudre ce problème, utilisez des noms en respectant la casse et l’orthographe.

- Projet qui utilise l' [incorporation de fonction](../../error-messages/tool-errors/function-inlining-problems.md). Cela peut se produire lorsque vous définissez les fonctions comme `inline` dans un fichier source, plutôt que dans un fichier d’en-tête. Les fonctions inline ne peuvent pas être vues en dehors du fichier source qui les définit. Pour résoudre ce problème, définissez les fonctions inline dans les en-têtes où elles sont déclarées.

- Appel d’une fonction C à C++ partir d’un programme sans utiliser une déclaration de `extern "C"` pour la fonction c. Le compilateur utilise des conventions d’affectation de noms de symboles C++ internes différentes pour C et le code. Le nom du symbole interne est ce que recherche l’éditeur de liens lors de la résolution des symboles. Pour résoudre ce problème, utilisez un wrapper `extern "C"` autour de toutes les déclarations de fonctions C utilisées C++ dans votre code, ce qui amène le compilateur à utiliser la Convention d’affectation de noms interne C pour ces symboles. Les options du compilateur [/TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) et [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) forcent le compilateur à C++ compiler les fichiers en tant que ou C, respectivement, quelle que soit l’extension de nom de fichier. Ces options peuvent entraîner des noms de fonctions internes différents de ceux attendus.

- Tentative de référencement de fonctions ou de données qui n’ont pas de liaison externe. Dans C++, les fonctions inline et les données de `const` ont une liaison interne, sauf spécification explicite comme `extern`. Pour résoudre ce problème, utilisez des déclarations de `extern` explicites sur les symboles référencés en dehors du fichier source de définition.

- [Corps de fonction manquant ou](../../error-messages/tool-errors/missing-function-body-or-variable.md) définition de variable. Cette erreur est courante lorsque vous déclarez, mais ne définissez pas, des variables, des fonctions ou des classes dans votre code. Le compilateur a uniquement besoin d’un prototype de fonction ou d' `extern` déclaration de variable pour générer un fichier objet sans erreur, mais l’éditeur de liens ne peut pas résoudre un appel à la fonction ou une référence à la variable, car aucun code de fonction ou espace de variable n’est réservé. Pour résoudre ce problème, veillez à définir toutes les fonctions et toutes les variables référencées dans un fichier source ou une bibliothèque que vous liez.

- Appel de fonction qui utilise des types de retours et de paramètres ou des conventions d’appel qui ne correspondent pas à celles de la définition de fonction. Dans C++ les fichiers objets, la [décoration de nom](../../error-messages/tool-errors/name-decoration.md) encode la Convention d’appel, la portée de la classe ou de l’espace de noms, ainsi que les types de retour et de paramètre d’une fonction. La chaîne encodée devient partie intégrante du nom de fonction décoré final. Ce nom est utilisé par l’éditeur de liens pour résoudre, ou faire correspondre, les appels à la fonction à partir d’autres fichiers objets. Pour résoudre ce problème, assurez-vous que la déclaration de fonction, la définition et les appels utilisent tous les mêmes portées, types et conventions d’appel.

- C++code que vous appelez, lorsque vous incluez un prototype de fonction dans une définition de classe, mais n' [incluez pas l’implémentation](../../error-messages/tool-errors/missing-function-body-or-variable.md) de la fonction. Pour résoudre ce problème, assurez-vous de fournir une définition pour tous les membres de classe que vous appelez.

- Tentative d’appel d’une fonction virtuelle pure à partir d’une classe de base abstraite. Une fonction virtuelle pure n’a pas d’implémentation de classe de base. Pour résoudre ce problème, assurez-vous que toutes les fonctions virtuelles appelées sont implémentées.

- Tentative d’utilisation d’une variable déclarée dans une fonction ([une variable locale](../../error-messages/tool-errors/automatic-function-scope-variables.md)) en dehors de la portée de cette fonction. Pour résoudre ce problème, supprimez la référence à la variable qui n’est pas dans la portée, ou déplacez la variable vers une étendue supérieure.

- Lorsque vous générez une version Release d’un projet ATL, en générant un message indiquant que le code de démarrage du CRT est requis. Pour résoudre ce problème, effectuez l’une des opérations suivantes :

  - Supprimez `_ATL_MIN_CRT` de la liste des définitions de préprocesseur pour permettre l’inclusion du code de démarrage du CRT. Pour plus d’informations, consultez [général, page de propriétés (projet)](../../build/reference/general-property-page-project.md).

  - Si possible, supprimez les appels aux fonctions CRT qui requièrent le code de démarrage CRT. Utilisez plutôt leurs équivalents Win32. Par exemple, utilisez `lstrcmp` à la place de `strcmp`. Les fonctions connues qui requièrent le code de démarrage CRT sont certaines des fonctions de chaîne et de virgule flottante.

## <a name="consistency-issues"></a>Problèmes de cohérence

Il n’existe actuellement aucune norme [ C++ ](../../error-messages/tool-errors/name-decoration.md) pour la décoration de nom entre les fournisseurs de compilateur, ni même entre différentes versions du même compilateur. Les fichiers objets compilés avec des compilateurs différents ne peuvent pas utiliser le même schéma d’attribution de noms. Leur liaison peut provoquer l’erreur LNK2001.

Le mélange des options de compilation inline [et non inline](../../error-messages/tool-errors/function-inlining-problems.md) sur des modules différents peut causer LNK2001. Si une C++ bibliothèque est créée avec l’incorporation de fonction activée ( **/Ob1** ou **/OB2**), mais que le fichier d’en-tête correspondant décrivant les fonctions a désactivé l’incorporation (aucun mot clé `inline`), cette erreur se produit. Pour résoudre ce problème, définissez les fonctions `inline` dans le fichier d’en-tête que vous incluez dans d’autres fichiers sources.

Si vous utilisez la directive de compilateur `#pragma inline_depth`, assurez-vous d’avoir défini une [valeur supérieure ou égale à 2](../../error-messages/tool-errors/function-inlining-problems.md), et assurez-vous d’utiliser également l’option de compilateur [/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/OB2](../../build/reference/ob-inline-function-expansion.md) .

Cette erreur peut se produire si vous omettez l’option de lien/NOENTRY lorsque vous créez une DLL de ressource uniquement. Pour résoudre ce problème, ajoutez l’option/NOENTRY à la commande Link.

Cette erreur peut se produire si vous utilisez des paramètres/SUBSYSTEM ou/ENTRY incorrects dans votre projet. Par exemple, si vous écrivez une application console et spécifiez/SUBSYSTEM : WINDOWS, une erreur externe non résolue est générée pour `WinMain`. Pour résoudre ce problème, assurez-vous que vous avez mis en correspondance les options et le type de projet. Pour plus d’informations sur ces options et les points d’entrée, consultez les options de l’éditeur de liens [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) et [/entry](../../build/reference/entry-entry-point-symbol.md) .

## <a name="exported-def-file-symbol-issues"></a>Problèmes de symboles de fichier. def exportés

Cette erreur se produit lorsqu’une exportation listée dans un fichier. def est introuvable. Cela peut être dû au fait que l’exportation n’existe pas, qu’elle n’est pas C++ correctement orthographiée ou qu’elle utilise des noms décorés. Un fichier. def ne prend pas de noms décorés. Pour résoudre ce problème, supprimez les exportations inutiles et utilisez `extern "C"` les déclarations pour les symboles exportés.

## <a name="use-the-decorated-name-to-find-the-error"></a>Utiliser le nom décoré pour Rechercher l’erreur

Le C++ compilateur et l’éditeur de liens utilisent la [décoration des noms](../../error-messages/tool-errors/name-decoration.md), également appelée « gestion *des noms »* . La décoration de nom encode des informations supplémentaires sur le type d’une variable dans son nom de symbole. Le nom de symbole d’une fonction encode son type de retour, les types de paramètres, la portée et la Convention d’appel. Ce nom décoré est le nom de symbole que l’éditeur de liens recherche pour résoudre les symboles externes.

Une erreur de liaison peut se produire si la déclaration d’une fonction ou d’une variable ne correspond pas *exactement* à la définition de la fonction ou de la variable. Cela est dû au fait que toute différence devient une partie du nom de symbole à faire correspondre. L’erreur peut se produire même si le même fichier d’en-tête est utilisé à la fois dans le code appelant et dans le code de définition. Cela peut se produire si vous compilez les fichiers sources à l’aide d’indicateurs de compilateur différents. Par exemple, si votre code est compilé pour utiliser la Convention d’appel `__vectorcall`, mais que vous établissez un lien vers une bibliothèque qui s’attend à ce que les clients l’appellent à l’aide de la Convention d’appel par défaut `__cdecl` ou `__fastcall`. Dans ce cas, les symboles ne correspondent pas, car les conventions d’appel sont différentes.

Pour vous aider à trouver la cause, le message d’erreur vous indique deux versions du nom. Il affiche à la fois le nom convivial, le nom utilisé dans le code source et le nom décoré (entre parenthèses). Vous n’avez pas besoin de savoir comment interpréter le nom décoré. Vous pouvez toujours Rechercher et le comparer à d’autres noms décorés. Les outils en ligne de commande peuvent vous aider à rechercher et à comparer le nom de symbole attendu et le nom de symbole réel :

- Les options [/exports](../../build/reference/dash-exports.md) et [/Symbols](../../build/reference/symbols.md) de l’outil en ligne de commande DUMPBIN sont utiles ici. Ils peuvent vous aider à identifier les symboles qui sont définis dans vos fichiers. dll et objets ou bibliothèques. Vous pouvez utiliser la liste de symboles pour vérifier que les noms décorés exportés correspondent aux noms décorés que l’éditeur de liens recherche.

- Dans certains cas, l’éditeur de liens peut uniquement signaler le nom décoré d’un symbole. Vous pouvez utiliser l’outil en ligne de commande UNDNAME pour obtenir la forme non décorée d’un nom décoré.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations, consultez la Stack Overflow question [« qu’est-ce qu’une erreur de symbole externe non définie/non résolue et comment la corriger ? »](https://stackoverflow.com/q/12573816/2002113).
