---
description: 'En savoir plus sur : TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++'
title: 'TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++'
ms.date: 11/04/2016
f1_keywords:
- vc.resources
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
ms.openlocfilehash: 347c816040d6e20cd9b7ee01f07662066981b8aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215467"
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035 : utilisation de plusieurs fichiers de ressources et fichiers d’en-tête avec Visual C++

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette remarque décrit comment l'éditeur de ressources Visual C++ prend en charge plusieurs fichiers de ressources et fichiers d'en-tête partagés dans un même projet ou parmi plusieurs projets, et comment tirer parti de cette prise en charge. Cette note répond à ces questions :

- Quand voulez-vous fractionner un projet en plusieurs fichiers de ressources et/ou fichiers d’en-tête, et comment procéder ?

- Comment partager un en-tête commun. Fichier H entre deux. Fichiers RC

- Comment divisez les ressources de projet en plusieurs. Fichiers RC

- Comment faire (et les outils) gérer les dépendances de build entre. RC,. CPP, et. Fichiers H

Vous devez savoir que si vous ajoutez un fichier de ressources supplémentaire à votre projet, l'Assistant ne reconnaît pas les ressources dans le fichier ajouté.

Cette note est structurée pour répondre aux questions ci-dessus comme suit :

- **Vue d’ensemble de la façon dont Visual C++ gère les fichiers de ressources et les fichiers d’en-tête** fournit une vue d’ensemble de la façon dont l’ensemble de ressources inclut la commande dans Visual C++ vous permet d’utiliser plusieurs fichiers de ressources et fichiers d’en-tête dans le même projet

- **Analyse de créé par AppWizard. RC et. H** examine les fichiers de ressources et d’en-tête multiples utilisés par une application créée par AppWizard. Ces fichiers constituent un bon modèle pour les fichiers de ressources et les fichiers d'en-tête supplémentaires que vous pourriez souhaiter ajouter à votre projet.

- L' **inclusion de fichiers d’en-tête supplémentaires** explique où vous pouvez inclure plusieurs fichiers d’en-tête et fournit des détails sur la procédure à suivre.

- **Partage d’un fichier d’en-tête entre deux. Les fichiers RC** montrent comment vous pouvez partager un fichier d’en-tête entre plusieurs. Des fichiers RC dans des projets différents, ou peut-être dans le même projet.

- **L’utilisation de plusieurs fichiers de ressources dans le même projet** explique où vous pouvez diviser votre projet en plusieurs. Les fichiers RC et fournissent des détails sur la procédure à suivre.

- L' **application de fichiers de Visual C++ non modifiables** décrit comment vous pouvez vous assurer Visual C++ ne modifie pas et ne reformate pas intentionnellement une ressource personnalisée.

- **Gestion des symboles partagés par plusieurs Visual C++ modifiés. Les fichiers RC** décrivent comment partager les mêmes symboles sur plusieurs. Fichiers RC et comment éviter d’assigner des valeurs numériques d’ID en double.

- **Gestion des dépendances entre. RC,. CPP, et. Les fichiers H** décrivent comment Visual C++ évite la recompilation inutile. CPP qui sont dépendants des fichiers de symboles de ressource.

- **Comment Visual C++ gère set includes informations** fournit des détails techniques sur la façon dont Visual C++ effectue le suivi de plusieurs (imbriquées). Fichiers RC et plusieurs fichiers d’en-tête #include par un. Fichier RC.

## <a name="overview-of-how-visual-c-manages-resource-files-and-header-files"></a>Vue d'ensemble de la façon dont Visual C++ gère les fichiers de ressources et les fichiers d'en-tête

Visual C++ gère un fichier de ressources .RC unique et un fichier d'en-tête .H correspondant en tant que paire de fichiers fortement couplée. Lorsque vous modifiez et enregistrez des ressources dans un fichier .RC, vous modifiez et enregistrez indirectement les symboles dans le fichier .H correspondant. Bien que vous puissiez ouvrir et modifier plusieurs fichiers .RC à la fois (via l'interface utilisateur MDI de Visual C++), pour tout fichier .RC donné vous modifiez indirectement exactement un fichier d'en-tête correspondant.

### <a name="symbol-header-file"></a>Fichier d'en-tête de symbole

Par défaut, Visual C++ nomme toujours le fichier d'en-tête correspondant RESOURCE.H, quel que soit le nom du fichier de ressources (par exemple, MYAPP.RC). À l’aide de la commande **Resource includes** du menu **affichage** dans Visual C++, vous pouvez modifier le nom de ce fichier d’en-tête en mettant à jour le fichier d’en-tête de symbole dans la boîte de dialogue **set includes** .

### <a name="read-only-symbol-directives"></a>Directives de symboles en lecture seule

Bien que Visual C++ modifie un seul fichier d'en-tête pour tout fichier .RC donné, Visual C++ prend en charge les références aux symboles définis dans des fichiers d'en-tête en lecture seule supplémentaires. À l’aide de la commande **Resource includes** du menu **affichage** dans Visual C++, vous pouvez spécifier un nombre quelconque de fichiers d’en-tête en lecture seule supplémentaires comme Read-Only directives de symboles. La restriction « lecture seule » signifie que lorsque vous ajoutez une nouvelle ressource au fichier .RC, vous pouvez utiliser un symbole défini dans le fichier d'en-tête en lecture seule ; mais si vous supprimez la ressource, le symbole reste défini dans le fichier d'en-tête en lecture seule. Vous ne pouvez pas modifier la valeur numérique assignée à un symbole en lecture seule.

### <a name="compile-time-directives"></a>Directives au moment de la compilation

Visual C++ prend également en charge l'imbrication des fichiers de ressources, où un fichier .RC est inclus (avec #include) dans un autre. Lorsque vous modifiez un fichier .RC donné avec Visual C++, aucune des ressources contenues dans les fichiers inclus n'est visible. Mais lorsque vous compilez le fichier .RC, les fichiers inclus sont également compilés. À l’aide de la commande **Resource includes** du menu **affichage** dans Visual C++, vous pouvez spécifier un nombre quelconque de #include. Fichiers RC en tant que directives de Compile-Time.

Notez ce qui se produit si vous lisez dans Visual C++ un. Fichier RC qui #include est un autre. Fichier RC qui n’est *pas* spécifié en tant que directive Compile-Time. Cette situation peut survenir lorsque vous importez dans Visual C++ un fichier .RC dont vous avez auparavant effectué la maintenance manuellement avec un éditeur de texte. Lorsque Visual C++ lit le fichier .RC inclus, il fusionne les ressources incluses dans le fichier .RC parent. Lorsque vous enregistrez le fichier .RC parent, l'instruction #include est remplacée par les ressources incluses. Si vous ne souhaitez pas que cette fusion se produise, vous devez supprimer l’instruction #include du parent. Fichier RC *avant* de le lire dans Visual C++; Ensuite, à l’aide de Visual C++, ajoutez la même instruction #include en tant que directive Compile-Time.

Visual C++ enregistre dans un. Fichier RC les trois genres ci-dessus incluent des informations (fichier d’en-tête de symbole, directives de symboles Read-Only et directives de Compile-Time) dans les directives #include *et les* ressources TEXTINCLUDE. Les ressources TEXTINCLUDE, un détail d’implémentation que vous n’avez normalement pas besoin de gérer, sont expliquées dans [comment Visual C++ gère Set comprend des informations](#_mfcnotes_tn035_set_includes).

## <a name="analysis-of-appwizard-created-rc-and-h-files"></a>Analyse des fichiers .RC et .H créés par AppWizard

L'examen du code d'application produit par AppWizard permet d'en savoir plus sur la manière dont Visual C++ gère plusieurs fichiers de ressources et fichiers d'en-tête. Les extraits de code examinés ci-dessous proviennent d'une application MYAPP produite par AppWizard à l'aide des options par défaut.

Une application créée par AppWizard utilise plusieurs fichiers de ressources et plusieurs fichiers d'en-tête, comme le résume le diagramme ci-dessous :

```Diagram
   RESOURCE.H     AFXRES.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2
        AFXRES.RC
        AFXPRINT.RC
```

Vous pouvez afficher ces multiples relations de fichiers à l'aide de la commande File/Set Includes de Visual C++.

MyApp. Release
Fichier de ressources de l'application que vous modifiez en Visual C++.

RESOURCE.H est le fichier d'en-tête spécifique à l'application. Il est toujours nommé RESOURCE.H par AppWizard, afin de rester cohérent avec le nom du fichier d'en-tête attribué par défaut par Visual C++. L'instruction #include pour ce fichier d'en-tête est la première instruction dans le fichier de ressources (MYAPP.RC) :

```rc
//Microsoft Visual C++ generated resource script
//
#include "resource.h"
```

RES\MYAPP. Postérieur
Contient des ressources qui ne seront pas modifiées par Visual C++ mais qui seront incluses dans le fichier .EXE compilé final. AppWizard ne crée pas ce genre de ressource par défaut, car Visual C++ peut modifier toutes les ressources standard, y compris la ressource de version (il s’agit d’une nouvelle fonctionnalité dans cette mise en production). Un fichier vide est généré par AppWizard au cas où vous souhaiteriez ajouter vos propres ressources mises en forme personnalisées à ce fichier.

Si vous utilisez des ressources mises en forme personnalisés, vous pouvez les ajouter à RES\MYAPP.RC2 et les modifier dans l'éditeur de texte Visual C++.

AFXRES.RC et AFXPRINT.RC contiennent les ressources standard requises par certaines fonctionnalités de l’infrastructure. Comme RES\MYAPP.RC2, ces deux fichiers de ressources fournis par l’infrastructure sont inclus (avec #include) à la fin de MYAPP.RC et ils sont spécifiés dans les directives au moment de la compilation de la boîte de dialogue Set Includes. Ainsi, vous ne visualisez pas ou ne modifiez pas directement ces ressources d'infrastructure pendant que vous modifiez MYAPP.RC dans Visual C++, mais elles sont compilées dans le fichier .RES binaire et le fichier .EXE final de l'application. Pour plus d’informations sur les ressources d’infrastructure standard, y compris les procédures de modification, consultez la [note technique 23](../mfc/tn023-standard-mfc-resources.md).

AFXRES.H définit des symboles standard, par exemple `ID_FILE_NEW`, utilisés par l'infrastructure et spécifiquement dans AFXRES.RC. AFXRES.H inclut également WINRES.H, qui contient un sous-ensemble de WINDOWS.H requis par les fichiers .RC générés par Visual C++, ainsi que par AFXRES.RC. Les symboles définis dans AFXRES.H sont disponibles lorsque vous modifiez le fichier de ressources d'application (MYAPP.RC). Par exemple, `ID_FILE_NEW` est utilisé pour l'élément Nouveau du menu Fichier dans la ressource de menu de MYAPP.RC. Vous ne pouvez pas modifier ou supprimer ces symboles définis par l'infrastructure.

## <a name="including-additional-header-files"></a><a name="_mfcnotes_tn035_including"></a> Inclusion de fichiers d’en-tête supplémentaires

L'application créée par AppWizard inclut uniquement deux fichiers d'en-tête : RESOURCE.H et AFXRES.H. Seul RESOURCE.H est spécifique à l'application. Vous devrez peut-être inclure des fichiers d'en-tête en lecture seule supplémentaires dans les cas suivants :

Le fichier d'en-tête est fourni par une source externe ou vous souhaitez partager le fichier d'en-tête entre plusieurs projets ou plusieurs parties du même projet.

Le fichier d'en-tête comporte une mise en forme et des commentaires que vous ne souhaitez pas que Visual C++ modifie ou filtre lors de l'enregistrement du fichier. Par exemple, vous souhaitez peut-être conserver des #define qui utilisent une arithmétique symbolique telle que :

```h
#define RED 0
#define BLUE 1
#define GREEN 2
#define ID_COLOR_BUTTON 1001
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)
```

Vous pouvez inclure des fichiers d’en-tête en lecture seule supplémentaires à l’aide de la commande **Resource includes** pour spécifier l’instruction #include en tant que deuxième directive Read-Only Symbol, comme dans :

```rc
#include "afxres.h"
#include "second.h"
```

Le nouveau diagramme des relations de fichiers se présente désormais comme suit :

```Diagram
                   AFXRES.H
    RESOURCE.H     SECOND.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2  
        AFXRES.RC
        AFXPRINT.RC
```

## <a name="sharing-a-header-file-between-two-rc-files"></a>Partage d'un fichier d'en-tête entre deux fichiers .RC

Vous pouvez partager un fichier d'en-tête entre deux fichiers .RC qui sont dans des projets différents, ou éventuellement dans le même projet. Pour cela, appliquez simplement la technique de directives en lecture seule décrite ci-dessus aux deux fichiers .RC. Dans le cas où les deux fichiers .RC concernent différentes applications (différents projets), le résultat est illustré dans le diagramme suivant :

```Diagram
     RESOURCE.H   AFXRES.H   RESOURCE.H  
    (for MYAPP1)  SECOND.H   (for MYAPP2)
          \       /     \       /
           \     /       \     /
          MYAPP1.RC      MYAPP2.RC
           /    \        /     \
          /      \      /       \
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2
                AFXPRINT.RC
```

Le scénario selon lequel le deuxième fichier d'en-tête est partagé par deux fichiers .RC dans la même application (projet) est décrit ci-dessous.

## <a name="using-multiple-resource-files-in-the-same-project"></a>Utilisation de plusieurs fichiers de ressources dans le même projet

Visual C++ et le compilateur de ressources prennent en charge plusieurs fichiers .RC dans le même projet via des instructions #include d'un fichier .RC dans un autre. L'imbrication multiple est autorisée. Il existe différentes raisons de fractionner les ressources de votre projet en plusieurs fichiers .RC :

- Il est plus facile de gérer un grand nombre de ressources entre plusieurs membres d’équipe de projet si vous fractionnez les ressources en plusieurs fichiers .RC. Si vous utilisez un package de gestion de contrôle de code source pour extraire les fichiers et archiver les modifications, le fractionnement des ressources en plusieurs fichiers .RC offre un contrôle plus fin de la gestion des modifications apportées aux ressources.

- Si vous souhaitez utiliser des directives du préprocesseur, telles que #ifdef, #endif et #define, pour certaines parties de vos ressources, vous devez les isoler dans des ressources en lecture seule qui seront compilées par le compilateur de ressources.

- Les fichiers .RC composants seront chargés et enregistrés plus rapidement dans Visual C++ qu'un fichier .RC composite.

- Si vous souhaitez effectuer la maintenance d'une ressource avec un éditeur de texte sous forme lisible, vous devez la conserver dans un fichier .RC distinct de celui modifié par Visual C++.

- Si vous devez conserver une ressource définie par l'utilisateur sous forme binaire ou texte interprétable par un autre éditeur de données spécialisé, vous devez la conserver dans un fichier .RC distinct afin que Visual C++ ne modifie pas le format en données hexadécimales. La. Les ressources de fichiers WAV (audio) dans les concepts avancés MFC, exemples [SPEAKN](../overview/visual-cpp-samples.md) , sont un bon exemple.

Vous pouvez inclure (avec #include) un SECOND.RC dans les directives de compilation dans la boîte de dialogue Set Includes :

```h
#include "res\myapp.rc2"  // non-Visual C++ edited resources
#include "second.rc"  // THE SECOND .RC FILE

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
```

Le résultat est illustré dans le diagramme ci-dessous :

```Diagram
   RESOURCE.H     AFXRES.H
          \       /
           \     /
          MYAPP.RC
              |
              |
        RES\MYAPP.RC2
        SECOND.RC  
        AFXRES.RC
        AFXPRINT.RC
```

À l’aide de directives au moment de la compilation, vous pouvez organiser vos ressources modifiables et non modifiables dans Visual C++ en plusieurs fichiers .RC, où le MYAPP.RC « Maître » ne fait rien d’autre que d’inclure les autres fichiers .RC. Si vous utilisez un projet Visual Studio C++. Fichier MAK, vous devez inclure le « maître ». RC dans le projet afin que toutes les #include ressources soient compilées avec votre application.

## <a name="enforcement-of-noneditable-visual-c-files"></a>Application des fichiers Visual C++ non modifiables

RES\MYAPP. créé par AppWizard Le fichier RC2 est un exemple de fichier contenant des ressources que vous ne souhaitez *pas* lire accidentellement dans Visual C++, puis le réécrire avec perte d’informations de mise en forme. Pour vous protéger contre cela, insérez les lignes suivantes au début du fichier RES\MYAPP.RC2 :

```rc2
#ifdef APSTUDIO_INVOKED
    #error this file is not editable by Visual C++
#endif //APSTUDIO_INVOKED
```

Lorsque Visual C++ compile. Fichier RC, il définit `APSTUDIO_INVOKED` aussi bien que `RC_INVOKED` . Si la structure de fichiers créée par AppWizard est endommagée et que Visual C++ lit la ligne #error ci-dessus, il signale une erreur irrécupérable et abandonne la lecture du fichier .RC.

## <a name="managing-symbols-shared-by-multiple-visual-c-edited-rc-files"></a>Gestion des symboles partagés par plusieurs fichiers .RC modifiés par Visual C++

Deux problèmes surviennent lorsque vous fractionnez vos ressources en plusieurs fichiers .RC que vous souhaitez modifier séparément dans Visual C++ :

- Vous pourriez souhaiter partager les mêmes symboles dans plusieurs fichiers .RC.

- Vous devez faire en sorte que Visual C++ évite d'assigner les mêmes valeurs numériques d'ID à des ressources distinctes (symboles).

Le diagramme suivant illustre une organisation de fichiers .RC et .H qui aborde le premier problème :

```Diagram
              MYAPP.RC
             /         \
            /           \
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H
     \    /    /      \   \    \
      \  /    /        \   \    \
      MYSTRS.RC         MYMENUS.RC
```

Dans cet exemple, les ressources de type chaîne sont conservées dans un fichier de ressources, MYSTRS.RC, et les menus sont conservés dans un autre, MYMENUS.RC. Certains symboles, par exemple pour les commandes, peuvent devoir être partagés entre les deux fichiers. Par exemple, un ID_TOOLS_SPELL peut être l'ID de commande de menu pour l'élément Vérifier l'orthographe dans un menu Outils et il peut également être l'ID de chaîne de l'invite de commandes affichée par l'infrastructure dans la barre d'état de la fenêtre principale de l'application.

Le symbole ID_TOOLS_SPELL est conservé dans le fichier d'en-tête partagé, MYSHARED.H. Vous effectuez la maintenance manuelle de ce fichier d'en-tête partagé avec un éditeur de texte ; Visual C++ ne le modifie pas directement. Dans les deux fichiers de ressources MYSTRS. RC et MYMENUS. RC, vous spécifiez #include MYSHARED. H dans les directives de Read-Only pour MYAPP. RC, à l’aide de la commande **Resource includes** , comme décrit précédemment.

Il est plus pratique d’anticiper un symbole que vous partagerez avant de tenter de l’utiliser pour identifier une ressource. Ajoutez le symbole au fichier d'en-tête partagé et, si vous n'avez pas encore inclus (avec #include) le fichier d'en-tête partagé dans les directives en lecture seule du fichier .RC, faites-le avant d'utiliser le symbole. Si vous ne prévoyez pas de partager le symbole de cette façon, vous devez déplacer manuellement (avec un éditeur de texte) l‘instruction #define pour le symbole, par exemple de MYMENUS.H vers MYSHARED.H, avant de l‘utiliser dans MYSTRS.RC.

Lorsque vous gérez des symboles dans plusieurs fichiers .RC, vous devez également faire en sorte que Visual C++ évite d'assigner les mêmes valeurs numériques d'ID à des ressources distinctes (symboles). Pour tout fichier .RC donné, Visual C++ assigne façon incrémentielle des ID dans quatre domaines d'identification. Entre les sessions d'édition, Visual C++ assure le suivi du dernier ID qu'il a assigné dans chacun des domaines dans le fichier d'en-tête de symbole pour le fichier .RC. Voici quelles sont les valeurs d'APS_NEXT pour un fichier .RC vide (nouveau) :

```rc
#define _APS_NEXT_RESOURCE_VALUE  101
#define _APS_NEXT_COMMAND_VALUE   40001
#define _APS_NEXT_CONTROL_VALUE   1000
#define _APS_NEXT_SYMED_VALUE     101
```

`_APS_NEXT_RESOURCE_VALUE` valeur de symbole suivante qui sera utilisée pour une ressource de boîte de dialogue, une ressource de menu, et ainsi de suite. La plage valide des valeurs de symboles de ressources est comprise entre 1 et 0x6FFF.

`_APS_NEXT_COMMAND_VALUE` valeur de symbole suivante qui sera utilisée pour l’identification d’une commande. La plage valide des valeurs de symboles de commandes est comprise entre 0x8000 et 0xDFFF.

`_APS_NEXT_CONTROL_VALUE` valeur de symbole suivante qui sera utilisée pour un contrôle de boîte de dialogue. La plage valide des valeurs de symboles de contrôles de boîtes de dialogue est comprise entre 8 et 0xDFFF.

`_APS_NEXT_SYMED_VALUE` est la valeur de symbole suivante qui sera émise lorsque vous affecterez manuellement une valeur de symbole à l’aide de la commande nouveau dans l’Explorateur de symboles.

Visual C++ commence avec des valeurs légèrement supérieures à la valeur la plus basse autorisée lors de la création d'un fichier .RC. AppWizard initialise également ces valeurs à quelque chose de plus approprié pour les applications MFC. Pour plus d’informations sur les plages de valeurs d’ID, consultez [Technical note 20](../mfc/tn020-id-naming-and-numbering-conventions.md).

À présent, chaque fois que vous créez un nouveau fichier de ressources, même dans le même projet, Visual C++ définit les mêmes `_APS_NEXT_` valeurs. Cela signifie que si vous ajoutez par exemple plusieurs boîtes de dialogue dans deux fichiers .RC différents, il est très probable que la même valeur #define soit assignée à différentes boîtes de dialogue. Par exemple, le même nombre, 101, peut être assigné à IDD_MY_DLG1 dans le premier fichier .RC et à IDD_MY_DLG2 dans un deuxième fichier .RC.

Pour éviter cela, vous devez réserver une plage numérique distincte pour chacun des quatre domaines d'ID dans les fichiers .RC respectifs. Pour ce faire, mettez à jour manuellement les `_APS_NEXT` valeurs dans chacun des. RC **avant** de commencer à ajouter des ressources. Par exemple, si la première. Le fichier RC utilise les `_APS_NEXT` valeurs par défaut, mais vous pouvez assigner les `_APS_NEXT` valeurs suivantes à la seconde. Fichier RC :

```rc
#define _APS_NEXT_RESOURCE_VALUE  2000
#define _APS_NEXT_COMMAND_VALUE   42000
#define _APS_NEXT_CONTROL_VALUE   2000
#define _APS_NEXT_SYMED_VALUE     2000
```

Naturellement, il est toujours possible que Visual C++ assigne une telle quantité d'ID dans le premier fichier .RC que les valeurs numériques commencent à chevaucher celles réservées pour le deuxième fichier .RC. Vous devez réserver des plages suffisamment étendues afin que cela ne se produise pas.

## <a name="managing-dependencies-between-rc-cpp-and-h-files"></a>Gestion des dépendances entre fichiers .RC, .CPP et .H

Lorsque Visual C++ enregistre un fichier .RC, il enregistre également les modifications de symboles dans le fichier RESOURCE.H correspondant. Tous vos fichiers .CPP qui font référence à des ressources dans le fichier .RC doivent inclure (avec #include) le fichier RESOURCE.H, généralement depuis le fichier d'en-tête maître de votre projet. Cela produit un effet secondaire indésirable, en raison de la gestion de projet interne de l'environnement de développement qui analyse les fichiers sources à la recherche de dépendances d'en-têtes. Chaque fois que vous ajoutez un nouveau symbole dans Visual C++, tous les. Fichiers CPP qui #include ressource. H doit être recompilé.

Visual C++ contourne la dépendance vis-à-vis de RESOURCE.H en incluant le commentaire suivant comme première ligne du fichier RESOURCE.H :

```h
//{{NO_DEPENDENCIES}}
```

L'environnement de développement interprète ce commentaire en ignorant les modifications apportées à RESOURCE.H, afin que les fichiers .CPP dépendants n'aient pas besoin d'être recompilés.

Visual C++ ajoute toujours la ligne de commentaire //{{NO_DEPENDENCIES}} à un fichier .RC lorsqu'il enregistre le fichier. Dans certains cas, le contournement de la dépendance de build vis-à-vis de RESOURCE.H peut provoquer des erreurs d'exécution non détectées au moment de la liaison. Par exemple, si vous utilisez le navigateur de symbole pour modifier la valeur numérique assignée à un symbole pour une ressource, celle-ci ne sera pas correctement détectée et chargée lors de l'exécution de l'application si le fichier .CPP faisant référence à la ressource n'est pas recompilé. Dans ce cas, vous devez recompiler explicitement any. Les fichiers CPP que vous connaissez sont affectés par les modifications de symboles dans la ressource. H ou sélectionnez **régénérer tout**. Si vous avez besoin de modifier fréquemment les valeurs de symboles pour un certain groupe de ressources, vous trouverez probablement plus pratique et plus sûr de décomposer ces symboles dans un fichier d’en-tête en lecture seule distinct, comme décrit dans la section précédente, [y compris des fichiers d’en-tête supplémentaires](#_mfcnotes_tn035_including).

## <a name="how-visual-c-manages-set-includes-information"></a><a name="_mfcnotes_tn035_set_includes"></a> Comment Visual C++ gère le jeu d’informations include

Comme décrit ci-dessus, la commande Set Includes du menu Fichier vous permet de spécifier trois types d'informations :

- Fichier d'en-tête de symbole

- Directives de symboles en lecture seule

- Directives au moment de la compilation

La section suivante décrit comment Visual C++ assure la maintenance de ces informations dans un fichier .RC. Vous n’avez pas besoin de ces informations pour utiliser Visual C++, mais elles peuvent vous permettre d’approfondir vos connaissances et d’utiliser ainsi la fonctionnalité Set Includes avec davantage de confiance.

Chacun des trois types d'informations Set Includes ci-dessus est stocké dans le fichier .RC sous deux formes : (1) comme #include ou autres directives interprétables par le compilateur de ressources, et (2) comme ressources TEXTINCLUDE spéciales interprétables uniquement par Visual C++.

L’objectif de la ressource TEXTINCLUDE est de stocker en toute sécurité les informations include dans un formulaire qui peut être facilement présenté dans la boîte de dialogue **set includes** de Visual C++. TEXTINCLUDE est un *type de ressource* défini par Visual C++. Visual C++ reconnaît trois ressources TEXTINCLUDE spécifiques dont les numéros d'identification de ressources sont 1, 2 et 3 :

|ID de ressource TEXTINCLUDE|Type d'informations Set Includes|
|-----------------------------|--------------------------------------|
|1|Fichier d'en-tête de symbole|
|2|Directives de symboles en lecture seule|
|3|Directives au moment de la compilation|

Chacun des trois types d'informations Set Includes est illustré par les fichiers MYAPP.RC et RESOURCE.H par défaut créés par AppWizard, comme décrit ci-dessous. Les jetons \0 et "" supplémentaires entre les blocs BEGIN et END sont requis par la syntaxe RC pour spécifier respectivement les chaînes terminées par zéro et le double guillemet.

### <a name="symbol-header-file"></a>Fichier d'en-tête de symbole

La forme des informations de fichier d'en-tête de symbole interprétée par le compilateur de ressources est simplement une instruction #include :

```rc
#include "resource.h"
```

La ressource TEXTINCLUDE correspondante est :

```rc
1 TEXTINCLUDE DISCARDABLE
BEGIN
    "resource.h\0"
END
```

### <a name="read-only-symbol-directives"></a>Directives de symboles en lecture seule

Les directives de symboles en lecture seule sont incluses en haut de MYAPP.RC sous la forme suivante interprétable par le compilateur de ressources :

```rc
#include "afxres.h"
```

La ressource TEXTINCLUDE correspondante est :

```rc
2 TEXTINCLUDE DISCARDABLE
BEGIN
   "#include ""afxres.h""\r\n"
   "\0"
END
```

### <a name="compile-time-directives"></a>Directives au moment de la compilation

Les directives au moment de la compilation sont incluses à la fin de MYAPP.RC sous la forme suivante interprétable par le compilateur de ressources :

```rc
#ifndef APSTUDIO_INVOKED
///////////////////////
//
// From TEXTINCLUDE 3
//
#include "res\myapp.rc2"  // non-Visual C++ edited resources

#include "afxres.rc"  // Standard components
#include "afxprint.rc"  // printing/print preview resources
#endif  // not APSTUDIO_INVOKED
```

La directive #ifndef APSTUDIO_INVOKED fait en sorte que Visual C++ ignore les directives de compilation.

La ressource TEXTINCLUDE correspondante est :

```rc
3 TEXTINCLUDE DISCARDABLE
BEGIN
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"
"\r\n"
"#include ""afxres.rc""  // Standard components\r\n"
"#include ""afxprint.rc""  // printing/print preview resources\r\n"
"\0"
END
```

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)\
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
