---
title: Vue d’ensemble des problèmes de mise à niveau potentiels (Visual C++)
ms.date: 11/04/2016
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 16918a70d4ce56a7415c3a807485e72c085d1194
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775035"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Vue d’ensemble des problèmes de mise à niveau potentiels (Visual C++)

Au fil des années, le compilateur Microsoft Visual C++ a subi de nombreuses modifications, avec des changements apportés au langage C++ lui-même, à la bibliothèque C++ standard, à la bibliothèque Runtime C (CRT) et à d’autres bibliothèques telles que MFC et ATL. Ainsi, durant la mise à niveau d’une application à partir d’une version antérieure de Visual Studio, vous pouvez rencontrer des erreurs du compilateur et de l’éditeur de liens ainsi que des avertissements dans le code précédemment compilé correctement. Plus la base de code d’origine est ancienne, plus le risque de telles erreurs est élevé. Cette vue d’ensemble résume les classes les plus courantes des problèmes que vous êtes susceptible de rencontrer, et fournit des liens vers des informations plus détaillées.

> [!NOTE]
> Par le passé, nous avons recommandé que les mises à niveau couvrant plusieurs versions de Visual Studio soient effectuées de façon incrémentielle, une version à la fois. Nous ne conseillons plus cette démarche. Nous avons découvert qu’il est presque toujours plus simple d’effectuer la mise à niveau vers la version la plus récente de Visual Studio, quelle que soit l’ancienneté de la base de code.

Les questions ou commentaires concernant le processus de mise à niveau peuvent être envoyés à vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Dépendances de bibliothèque et d’ensemble d’outils

Quand vous mettez à niveau une application vers une nouvelle version de Visual Studio, il est vivement recommandé, et très souvent nécessaire, de mettre également à niveau toutes les bibliothèques et DLL auxquelles l’application est liée. Pour cela, vous devez avoir accès au code source ou le fournisseur de bibliothèque doit pouvoir fournir de nouveaux fichiers binaires compilés avec la même version principale du compilateur. Si l’une de ces conditions est remplie, vous pouvez ignorer cette section, qui aborde les détails de la compatibilité binaire. Si aucune de ces conditions n’est remplie, vous ne pourrez peut-être pas utiliser les bibliothèques dans votre application mise à niveau. Les informations contenues dans cette section vous permettront de savoir si vous pouvez poursuivre la mise à niveau.

### <a name="toolset"></a>Ensemble d'outils

Les formats de fichier .obj et .lib sont bien définis et rarement modifiés. Des éléments sont parfois ajoutés à ces formats de fichier, mais ces ajouts n’affectent généralement pas la capacité des ensembles d’outils plus récents de consommer les fichiers objets et les bibliothèques produits par des ensembles d’outils plus anciens. La seule exception notable ici concerne la compilation avec [/GL (optimisation de l’ensemble du programme)](../build/reference/gl-whole-program-optimization.md). Si vous compilez avec `/GL`, le fichier objet résultant peut uniquement être lié à l’aide de l’ensemble d’outils utilisé pour le produire. Ainsi, si vous produisez un fichier objet en utilisant `/GL` et le compilateur Visual Studio 2017 (v141), vous devez le lier à l’aide de l’éditeur de liens Visual Studio 2017 (v141). En effet, les structures de données internes dans les fichiers objets ne sont pas stables entre les versions principales de l’ensemble d’outils, et les ensembles d’outils les plus récents ne comprennent pas les anciens formats de données.

C++ ne dispose pas d’une interface ABI (Application Binary Interface) stable. Visual Studio gère une interface ABI C++ stable pour toutes les versions secondaires d’une version. Par exemple, Visual Studio 2017 et toutes ses mises à jour sont compatibles du point de vue binaire. Toutefois, l’interface ABI n’est pas obligatoirement compatible entre les versions principales de Visual Studio (à l’exception de 2015 et 2017, qui _sont_ compatibles du point de vue binaire). Autrement dit, nous pouvons apporter des modifications avec rupture à la disposition de type C++, à la décoration de nom, à la gestion des exceptions et à d’autres parties de l’interface ABI C++. Ainsi, si vous avez un fichier objet qui affiche des symboles externes avec une liaison C++, ce fichier objet peut ne pas être lié correctement aux fichiers objets générés avec une version principale différente de l’ensemble d’outils. Notez que l’expression « peut ne pas être lié » ici a plusieurs significations possibles : le lien peut échouer complètement (par exemple, si la décoration de nom a changé), le lien peut aboutir et les dysfonctionnements peuvent survenir au moment de l’exécution (par exemple, si la disposition de type a changé) ou tout fonctionne correctement dans de nombreux cas et aucun problème ne se pose. Notez également que si l’interface ABI C++ n’est pas stable, l’interface ABI C et le sous-ensemble de l’interface ABI C++ requis pour COM sont stables.

Si vous créez un lien à une bibliothèque d’importation, les versions ultérieures des bibliothèques redistribuables Visual Studio qui conservent une compatibilité avec l’ABI peuvent être utilisées lors de l’exécution. Par exemple, si votre application est compilée et liée à l’aide de l’ensemble d’outils Visual Studio 2015 Update 3, vous pouvez utiliser n’importe quel package redistribuable de Visual Studio 2017, car les bibliothèques 2015 et 2017 ont conservé une compatibilité binaire descendante. L’inverse n’est pas vrai : vous ne pouvez pas utiliser un package redistribuable d’une version antérieure de l’ensemble d’outils que vous avez utilisé pour générer votre code, même s’il a une ABI compatible.

### <a name="libraries"></a>Bibliothèques

Si vous compilez un fichier source à l’aide d’une version particulière des en-têtes de bibliothèques Visual Studio C++ (en utilisant #include sur les en-têtes), le fichier objet obtenu doit être lié avec la même version des bibliothèques. Ainsi, par exemple, si votre fichier source est compilé avec le fichier d’en-tête \<immintrin.h > Visual Studio 2015 Update 3, vous devez le lier avec la bibliothèque vcruntime Visual Studio 2015 Update 3. De même, si votre fichier source est compilé avec le fichier d’en-tête \<iostream> Visual Studio 2017 version 15.5, vous devez le lier avec la bibliothèque C++ standard Visual Studio 2017 version 15.5, msvcprt. Les associations ne sont pas prises en charge.

Pour la bibliothèque C++ standard, les associations ont été explicitement interdites via l’utilisation de `#pragma detect_mismatch` dans les en-têtes standard depuis Visual Studio 2010. Si vous tentez de lier des fichiers objets incompatibles ou d’effectuer une liaison avec la bibliothèque standard incorrecte, la liaison échoue.

Pour la bibliothèque CRT, les associations n’ont jamais été prises en charge, mais cela a souvent fonctionné, au moins jusqu’à Visual Studio 2015 et la bibliothèque Universal CRT, étant donné que la surface d’API n’a pas beaucoup changé dans le temps. La bibliothèque Universal CRT a révélé la compatibilité descendante pour que nous puissions la gérer à l’avenir. En d’autres termes, nous n’avons pas prévu d’introduire de nouveaux fichiers binaires Universal CRT avec version dans le futur. Au lieu de cela, la bibliothèque Universal CRT existante est désormais mise à jour sur place.

Pour assurer une compatibilité de liaison partielle avec les fichiers objets (et les bibliothèques) compilés avec des versions antérieures des en-têtes Runtime C de Microsoft, nous fournissons une bibliothèque, legacy_stdio_definitions.lib, avec Visual Studio 2015 et versions ultérieures. Cette bibliothèque fournit des symboles de compatibilité pour la plupart des fonctions et exportations de données qui ont été supprimées de la bibliothèque Universal CRT. L’ensemble des symboles de compatibilité fourni par legacy_stdio_definitions.lib est suffisant pour répondre à la plupart des dépendances, dont toutes les dépendances dans les bibliothèques incluses dans le SDK Windows. Toutefois, il existe des symboles qui ont été supprimés de la bibliothèque Universal CRT pour lesquels il n’est pas possible de fournir de tels symboles de compatibilité. Ces symboles incluent certaines fonctions (par exemple, \_\_iob\_func) et les exportations de données (par exemple, \_\_imp\_\_\_iob, \_\_imp\_\_\_pctype, \_\_imp\_\_\_mb\_cur\_max).

Si vous avez une bibliothèque statique qui a été générée avec une ancienne version des en-têtes Runtime C, nous vous recommandons d’effectuer les actions suivantes (dans cet ordre) :

1. Regénérez la bibliothèque statique à l’aide de Visual Studio 2017 et des en-têtes Universal CRT pour prendre en charge la liaison avec la bibliothèque Universal CRT. Il s’agit de l’option entièrement prise en charge (et donc de la meilleure).

1. Si vous ne pouvez pas (ou ne souhaitez pas) regénérer la bibliothèque statique, vous pouvez essayer la liaison avec legacy\_stdio\_definitions.lib. Si elle est suffisante pour les dépendances durant l’édition de liens de votre bibliothèque statique, vous devez tester minutieusement la bibliothèque statique comme elle utilisée dans le fichier binaire pour vérifier qu’elle n’est affectée de façon négative par aucun des [changements de comportement effectués dans la bibliothèque Universal CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Si les dépendances de votre bibliothèque statique ne sont pas satisfaites par legacy\_stdio\_definitions.lib ou si la bibliothèque ne fonctionne pas avec la bibliothèque Universal CRT en raison des changements de comportement mentionnés ci-dessus, nous vous recommandons d’encapsuler votre bibliothèque statique dans une DLL que vous liez avec la version appropriée du Runtime C de Microsoft. Par exemple, si la bibliothèque statique a été créée à l’aide de Visual Studio 2013, vous devez créer cette DLL à l’aide de Visual Studio 2013 et aussi des bibliothèques Visual Studio 2013 C++. Par la génération de la bibliothèque dans une DLL, vous encapsulez le détail d’implémentation qui est sa dépendance sur une version particulière du Runtime C de Microsoft. (Notez que vous devez veiller à ce que l’interface DLL ne « divulgue » pas les détails du Runtime C utilisé, par exemple en retournant FILE* sur la limite de DLL ou en retournant un pointeur alloué par malloc et en attendant que l’appelant le libère.)

L’utilisation de plusieurs bibliothèques CRT dans un processus unique ne pose pas de problème en soi (en effet, la plupart des processus finissent par charger plusieurs DLL CRT ; par exemple, les composants du système d’exploitation Windows dépendent de msvcrt.dll et le CLR dépend de sa propre bibliothèque CRT privée). Des problèmes surviennent quand vous mélangez l’état de différentes bibliothèques CRT. Par exemple, vous ne devez pas allouer de la mémoire à l’aide de msvcr110.dll!malloc et essayer de libérer cette mémoire à l’aide de msvcr120.dll!free, et vous ne devez pas essayer d’ouvrir un fichier à l’aide de msvcr110!fopen et essayer de le lire à l’aide de msvcr120!fread. Tant que vous ne mélangez pas l’état de différentes bibliothèques CRT, celles-ci peuvent être chargées en toute sécurité dans un processus unique.

Pour plus d’informations, consultez [Mettre à niveau votre code vers la bibliothèque Universal CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Erreurs dues aux paramètres de projet

Pour commencer le processus de mise à niveau, ouvrez simplement un projet /une solution / un espace de travail plus ancien dans la dernière version de Visual Studio. Visual Studio crée un projet basé sur les anciens paramètres de projet. Si l’ancien projet comporte des chemins d’accès de bibliothèque ou Include codés en dur vers des emplacements non standard, il est possible que les fichiers dans ces chemins ne soient pas visibles pour le compilateur quand le projet utilise les paramètres par défaut. Pour plus d’informations, consultez [Paramètre OutputFile de l’éditeur de liens](porting-guide-spy-increment.md#linker_output_settings).

En général, c’est maintenant le moment idéal d’organiser votre code de projet correctement afin de simplifier la gestion des projets et de lancer la compilation du code mis à niveau aussi rapidement que possible. Si votre code source est déjà bien organisé et que votre ancien projet est compilé avec Visual Studio 2010 ou version ultérieure, vous pouvez modifier manuellement le nouveau fichier projet pour prendre en charge la compilation à la fois sur l’ancien et le nouveau compilateurs. L’exemple suivant montre comment effectuer la compilation pour Visual Studio 2015 et Visual Studio 2017 :

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019 : Externes non résolues

Pour les symboles non résolus, vous devez peut-être corriger les paramètres de votre projet.

- Si le fichier source figure à un emplacement non défini par défaut, avez-vous ajouté le chemin d’accès aux répertoires Include du projet ?

- Si le symbole externe est défini dans un fichier .lib, avez-vous spécifié le chemin d’accès au fichier .lib dans les propriétés du projet et est-ce que la version correcte du fichier .lib s’y trouve réellement ?

- Tentez-vous d’établir une liaison à un fichier .lib qui a été compilé avec une autre version de Visual Studio ? Dans ce cas, consultez la section précédente sur les dépendances de bibliothèque et d’ensemble d’outils.

- Est-ce que les types des arguments du site d’appel correspondent réellement à une surcharge existante de la fonction ? Vérifiez que les types sous-jacents de tous les typedefs dans la signature de la fonction et dans le code qui appelle la fonction répondent à vos attentes.

Pour résoudre les erreurs de symboles non résolus, vous pouvez essayer d’utiliser dumpbin.exe pour examiner les symboles définis dans un fichier binaire. Essayez d’utiliser la ligne de commande ci-dessous pour afficher les symboles définis dans une bibliothèque :

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t est un type natif)

(Dans Microsoft Visual C++ 6.0 et les versions antérieures, **wchar_t** n’était pas implémenté en tant que type intégré, mais il était déclaré dans wchar.h en tant que typedef pour unsigned short.) Conformément à la norme C++, **wchar_t** doit être un type intégré. L’utilisation de la version typedef peut entraîner des problèmes de portabilité. Si vous effectuez une mise à niveau à partir de versions antérieures de Visual Studio et si vous rencontrez l’erreur de compilateur C2664, car le code essaie de convertir implicitement **wchar_t** en **unsigned short**, nous vous recommandons de changer le code pour corriger cette erreur, au lieu de définir `/Zc:wchar_t-`. Pour plus d’informations, consultez [/Zc:wchar_t (wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Mise à niveau avec les options de l’éditeur de liens /NODEFAULTLIB, /ENTRY et /NOENTRY

L’option d’éditeur de liens `/NODEFAULTLIB` (ou la propriété d’éditeur de liens Toutes bibliothèques par défaut ignorées) indique à l’éditeur de liens de ne pas établir de liaison automatiquement dans les bibliothèques par défaut, par exemple la bibliothèque CRT. Cela signifie que chaque bibliothèque doit être répertoriée individuellement comme entrée. Cette liste de bibliothèques est indiquée dans la propriété **Dépendances supplémentaires** de la section **Éditeur de liens** de la boîte de dialogue **Propriétés du projet**.

Les projets qui utilisent cette option posent un problème lors de la mise à niveau, car les noms de certaines des bibliothèques par défaut ont été modifiés. Comme chaque bibliothèque doit être répertoriée dans la propriété **Dépendances supplémentaires** ou sur la ligne de commande de l’éditeur de liens, vous devez mettre à jour la liste des bibliothèques pour utiliser les noms actuels.

Le tableau suivant présente les bibliothèques dont le nom a été modifié depuis Visual Studio 2015. Pour la mise à niveau, vous devez remplacer les noms de la première colonne par ceux de la deuxième colonne. Certaines de ces bibliothèques sont des bibliothèques d’importation, mais cela ne devrait pas avoir d’importance.

|||
|-|-|
|Si vous utilisiez :|Vous devez la remplacer par :|
|libcmt.lib|libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|ucrt.lib, vcruntime.lib|
|msvcrtd.lib|ucrtd.lib, vcruntimed.lib|

Le même problème se pose si vous utilisez les options `/ENTRY` ou `/NOENTRY`, qui ont également pour effet de contourner les bibliothèques par défaut.

## <a name="errors-due-to-improved-language-conformance"></a>Erreurs dues à la conformité au langage améliorée

Le compilateur Microsoft Visual C++ a constamment amélioré sa conformité à la norme C++ au fil des années. Le code compilé dans les versions antérieures peut ne pas être compilé dans Visual Studio 2017, car le compilateur signale de façon appropriée une erreur précédemment ignorée ou explicitement autorisée.

Par exemple, le commutateur `/Zc:forScope` a été introduit aux origines de MSVC. Il autorise un comportement non conforme pour les variables de boucle. Ce commutateur est maintenant déprécié et peut être supprimé dans les prochaines versions. Il est recommandé de ne pas utiliser ce commutateur lors de la mise à niveau de votre code. Pour plus d’informations, consultez [/Zc:forScope- est déprécié](porting-guide-spy-increment.md#deprecated_forscope).

Un argument non const passé à un paramètre const est un exemple d’erreur de compilateur courante que vous pouvez rencontrer lors de la mise à niveau. Les versions antérieures du compilateur ne signalaient pas toujours cela comme une erreur. Pour plus d’informations, consultez [Conversions plus strictes du compilateur](porting-guide-spy-increment.md#stricter_conversions).

Pour plus d’informations sur les améliorations apportées à la conformité, consultez [Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md) et [Améliorations de la conformité de C++ dans Visual Studio 2017](../overview/cpp-conformance-improvements-2017.md).

## <a name="errors-involving-stdinth-integral-types"></a>Erreurs impliquant les types intégraux \<stdint.h>

L’en-tête \<stdint.h> définit les typedefs et macros qui, contrairement aux types intégraux intégrés, ont forcément une longueur spécifiée sur toutes les plateformes. Voici des exemples : `uint32_t` et `int64_t`. L’en-tête \<stdint.h> a été ajouté dans Visual Studio 2010. Le code qui a été écrit avant 2010 peut avoir fourni des définitions privées pour ces types et ces définitions ne sont peut-être pas toujours cohérentes avec les définitions \<stdint.h>.

S’il s’agit de l’erreur C2371 et si un type `stdint` est impliqué, cela signifie probablement que le type est défini dans un en-tête de votre code ou dans un fichier lib tiers. Lors de la mise à niveau, vous devez supprimer toutes les définitions personnalisées des types \<stdint.h>, tout en les comparant d’abord aux définitions standard actuelles pour vous assurer de ne pas introduire de nouveaux problèmes.

Vous pouvez appuyer sur **F12** (**Atteindre la définition**) pour voir où le type en question est défini.

L’option de compilateur [/showIncludes](../build/reference/showincludes-list-include-files.md) peut être utile ici. Dans la boîte de dialogue **Pages de propriétés** de votre projet, ouvrez la page **C/C++** > **Avancé** et affectez la valeur **Oui** à **Affichage des fichiers Include**. Regénérez ensuite votre projet et consultez la liste des `#include` dans la fenêtre Sortie. Chaque en-tête est mis en retrait sous l’en-tête qui l’inclut.

## <a name="errors-involving-crt-functions"></a>Erreurs impliquant des fonctions CRT

De nombreuses modifications ont été apportées au Runtime C au fil des années. De nombreuses versions sécurisées de fonctions ont été ajoutées et certaines ont été supprimées. En outre, comme décrit précédemment dans cet article, l’implémentation Microsoft de la bibliothèque CRT a été refactorisée dans Visual Studio 2015 en nouveaux fichiers binaires et fichiers .lib associés.

Si une erreur implique une fonction CRT, effectuez des recherches dans [Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md) ou [Améliorations de la conformité de C++ dans Visual Studio 2017](../overview/cpp-conformance-improvements-2017.md) pour voir si ces rubriques contiennent des informations supplémentaires. S’il s’agit de l’erreur « LNK2019 : Symbole externe non résolu », vérifiez que la fonction n’a pas été supprimée. Sinon, si vous êtes sûr que la fonction existe toujours et si le code appelant est correct, vérifiez que le projet utilise `/NODEFAULTLIB`. Si tel est le cas, vous devez mettre à jour la liste des bibliothèques afin que le projet utilise les nouvelles bibliothèques Universal CRT. Pour plus d’informations, consultez la section ci-dessus sur les dépendances de bibliothèque.

Si l’erreur implique `printf` ou `scanf`, vérifiez que vous ne définissez pas de manière privée une fonction sans inclure stdio.h. Dans ce cas, supprimez les définitions privées ou établissez une liaison à legacy\_stdio\_definitions.lib. Vous pouvez le définir dans la boîte de dialogue **Pages de propriétés** sous **Propriétés de configuration** > **Éditeur de liens** > **Entrée**, dans la propriété **Dépendances supplémentaires**. Si vous établissez une liaison avec le SDK Windows 8.1 ou version antérieure, ajoutez legacy\_stdio\_definitions.lib.

Si l’erreur implique des arguments de chaîne de format, le compilateur est probablement plus strict sur l’application de la norme. Pour plus d’informations, consultez l’historique des modifications. Prêtez une attention toute particulière aux erreurs ici, car elles peuvent potentiellement représenter un risque pour la sécurité.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Erreurs dues à des modifications de la norme C++

La norme C++ elle-même a évolué et n’est désormais pas toujours à compatibilité descendante. L’introduction dans C++ 11 de la sémantique de mouvement, de nouveaux mots clés ainsi que d’autres fonctionnalités de langage et de bibliothèque standard est susceptible de provoquer des erreurs de compilateur et même un comportement différent au moment de l’exécution.

Par exemple, un ancien programme C++ peut inclure l’en-tête iostream.h. Cet en-tête a été déprécié au début de l’historique de C++ et a finalement été entièrement supprimé de Visual Studio. Dans ce cas, vous devez utiliser \<iostream> et réécrire votre code. Pour plus d’informations, consultez [Mise à jour de l’ancien code iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838 : Avertissement de conversion restrictive

La norme C++ indique désormais que les conversions entre les valeurs intégrales non signées et signées sont considérées comme des conversions restrictives. Le compilateur ne générait pas cet avertissement avant Visual Studio 2015. Vous devez examiner chaque occurrence pour vous assurer que la conversion restrictive n’a pas d’impact sur l’exactitude de votre code.

## <a name="warnings-to-use-secure-crt-functions"></a>Avertissements pour utiliser des fonctions CRT sécurisées

Au fil des années, des versions sécurisées de fonctions Runtime C ont été introduites. Bien que les anciennes versions non sécurisées soient toujours disponibles, il est recommandé de modifier votre code pour utiliser les versions sécurisées. Le compilateur émet un avertissement pour l’utilisation des versions non sécurisées. Vous pouvez choisir de désactiver ou d’ignorer ces avertissements. Pour désactiver l’avertissement pour tous les projets dans votre solution, ouvrez **View (Afficher)** > **Gestionnaire de propriétés**, sélectionnez tous les projets pour lesquels vous souhaitez désactiver l’avertissement, puis cliquez avec le bouton droit sur les éléments sélectionnés et choisissez **Propriétés**. Dans la boîte de dialogue **Pages de propriétés** sous **Propriétés de configuration** > **C/C++** > **Avancé**, Sélectionnez **Désactivation des avertissements spécifiques**. Cliquez sur la flèche déroulante, puis sur **Modifier**. Entrez 4996 dans la zone de texte. (N’incluez pas le préfixe « C ».) Pour plus d’informations, consultez [Portage pour utiliser les fonctions CRT sécurisées](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Erreurs dues à des modifications des API Windows ou à des SDK obsolètes

Au fil des années, des API Windows et des types de données ont été ajoutés, et parfois modifiés ou supprimés. En outre, d’autres SDK qui ne faisaient pas partie du système d’exploitation principal ont été ajoutés et supprimés. D’anciens programmes peuvent par conséquent contenir des appels à des API qui n’existent plus. Ils peuvent également contenir des appels à des API dans d’autres SDK Microsoft qui ne sont plus prises en charge. Si vous voyez une erreur impliquant une API Windows ou une API d’un ancien SDK Microsoft, il est possible qu’une API ait été supprimée et/ou remplacée par une fonction plus récente et plus sécurisée.

Pour plus d’informations sur l’ensemble API actuel et les versions de systèmes d’exploitation minimales prises en charge pour une API Windows spécifique, consultez [Catalogue de références et API Microsoft](https://msdn.microsoft.com/library) et accédez à l’API en question.

### <a name="windows-version"></a>Version Windows

Lors de la mise à niveau d’un programme qui utilise l’API Windows directement ou indirectement, vous devez décider de la version minimale de Windows à prendre en charge. Dans la plupart des cas, Windows 7 représente un choix judicieux. Pour plus d’informations, consultez [Problèmes liés aux fichiers d’en-tête](porting-guide-spy-increment.md#header_file_problems). La macro `WINVER` définit la plus ancienne version de Windows sur laquelle votre programme est conçu pour s’exécuter. Si votre programme MFC affecte à WINVER la valeur 0x0501 (Windows XP), un avertissement est émis, car MFC ne prend plus en charge XP, même si le compilateur lui-même a un mode XP.

Pour plus d’informations, consultez [Mise à jour de la version cible de Windows](porting-guide-spy-increment.md#updating_winver) et [Autres fichiers d’en-tête obsolètes](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL / MFC

ATL et MFC sont des API relativement stables, mais qui sont parfois modifiées. Pour plus d’informations, consultez [Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md), [Nouveautés de Visual C++ dans Visual Studio 2017](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) et [Améliorations de la conformité de C++ dans Visual Studio 2017](../overview/cpp-conformance-improvements-2017.md).

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK2005 : _DllMain@12 déjà défini dans MSVCRTD.lib

Cette erreur peut se produire dans les applications MFC. Elle indique un problème d’ordre incorrect entre la bibliothèque CRT et la bibliothèque MFC. La bibliothèque MFC doit être liée en premier pour pouvoir fournir les opérateurs new et delete. Pour corriger l’erreur, utilisez le commutateur `/NODEFAULTLIB` afin d’ignorer les bibliothèques par défaut suivantes : MSVCRTD.lib et mfcs140d.lib. Ajoutez ensuite ces mêmes bibliothèques comme dépendances supplémentaires.

## <a name="32-vs-64-bit"></a>32 bits et 64 bits

Si votre code d’origine est compilé pour les systèmes 32 bits, vous avez la possibilité de créer une version 64 bits à la place ou en plus d’une nouvelle application 32 bits. En général, vous devez d’abord lancer la compilation de votre programme en mode 32 bits, puis essayer en mode 64 bits. La compilation en mode 64 bits est simple, mais peut révéler dans certains cas des bogues qui étaient masqués par les builds 32 bits.

En outre, vous devez garder à l’esprit les éventuels problèmes lors de la compilation et de l’exécution relatifs à la taille du pointeur, aux valeurs de taille et date/heure ainsi qu’aux spécificateurs de format dans les fonctions printf et scanf. Pour plus d’informations, consultez [Configurer Visual C++ pour des cibles x64 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md) et [Problèmes courants de migration vers Visual C++ 64 bits](../build/common-visual-cpp-64-bit-migration-issues.md). Pour obtenir des conseils supplémentaires sur la migration, consultez [Guide de programmation pour Windows 64 bits](/windows/desktop/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode et MBCS/ASCII

Avant la standardisation d’Unicode, de nombreux programmes utilisaient le jeu de caractères multioctets (MBCS) pour représenter les caractères qui n’étaient pas inclus dans le jeu de caractères ASCII. Dans les anciens projets MFC, MBCS était le paramètre par défaut et, lors de la mise à niveau d’un tel programme, vous recevez des avertissements qui vous demandent d’utiliser Unicode à la place. Vous pouvez choisir de désactiver ou d’ignorer l’avertissement si vous pensez que la conversion au format Unicode ne vaut pas le coût de développement. Pour le désactiver pour tous les projets dans votre solution, ouvrez **View (Afficher)** > **Gestionnaire de propriétés**, sélectionnez tous les projets pour lesquels vous souhaitez désactiver l’avertissement, puis cliquez avec le bouton droit sur les éléments sélectionnés et choisissez **Propriétés**. Dans la boîte de dialogue **Pages de propriétés**, sélectionnez **Propriétés de configuration** > **C/C++** > **Avancé**. Dans la propriété **Désactivation des avertissements spécifiques**, ouvrez la flèche déroulante, puis choisissez **Modifier**. Entrez 4996 dans la zone de texte. (N’incluez pas le préfixe « C ».) Choisissez **OK** pour enregistrer la propriété, puis choisissez **OK** pour enregistrer vos modifications.

Pour plus d’informations, consultez [Portage de MBCS vers Unicode](porting-guide-spy-increment.md#porting_to_unicode). Pour plus d’informations d’ordre général sur MBCS et Unicode, consultez [Texte et chaînes en Visual C++](../text/text-and-strings-in-visual-cpp.md) et [Internationalisation](../c-runtime-library/internationalization.md).

## <a name="see-also"></a>Voir aussi

[Mise à niveau de projets à partir de versions antérieures de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio 2017](../overview/cpp-conformance-improvements-2017.md)