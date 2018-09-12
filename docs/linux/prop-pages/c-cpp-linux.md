---
title: C/C++, propriétés (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 7ab78284929de8e5991abb0d1a8c89ead500096a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314701"
---
# <a name="cc-properties-linux-c"></a>C/C++, propriétés (Linux C++)

## <a name="general"></a>Général

Property | Description | Options
--- | ---| ---
Autres répertoires Include | Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules. (-I[path]).
Format des informations de débogage | Indique le type d'informations de débogage générées par le compilateur. | **Aucune** : ne génère aucune information de débogage ; la compilation peut donc être plus rapide.<br/>**Informations de débogage minimales** : génère des informations de débogage minimales.<br/>**Informations de débogage complètes (DWARF2)**  : génère des informations de débogage DWARF2.<br/>
Nom de fichier objet | Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire. (-o [name]).
Niveau d’avertissement | Sélectionnez la rigueur avec laquelle le compilateur doit traiter les erreurs de code.  D’autres indicateurs doivent être ajoutés directement dans les options supplémentaires. (/w, /Weverything). | **Désactiver tous les avertissements** : désactive tous les avertissements du compilateur.<br/>**Activer tous les avertissements** : active tous les avertissements, dont ceux qui sont désactivés par défaut.<br/>
Considérer les avertissements comme des erreurs | Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il est conseillé d’utiliser /Werror dans toutes les compilations, car la résolution de tous les avertissements permet de réduire les erreurs de code difficilement détectables.
Avertissements supplémentaires C | Définit un ensemble de messages d’avertissement supplémentaires.
Avertissements supplémentaires C++ | Définit un ensemble de messages d’avertissement supplémentaires.
Activer le mode détaillé | Quand le mode détaillé est activé, cet outil affiche plus d’informations que pour le diagnostic de la build.
Compilateur C | Spécifie le programme à appeler durant la compilation de fichiers sources C, ou le chemin du compilateur C sur le système distant.
Compilateur C++ | Spécifie le programme à appeler durant la compilation de fichiers sources C++, ou le chemin du compilateur C++ sur le système distant.
Délai d’attente de la compilation | Délai d’attente de la compilation distante en millisecondes.
Copier les fichiers objets | Indique s’il faut copier les fichiers objets compilés du système distant sur la machine locale.

## <a name="optimization"></a>Optimisation

Property | Description | Options
--- | ---| ---
Optimisation | Indique le niveau d’optimisation pour l’application. | **Personnalisé** : optimisation personnalisée.<br/>**Désactivé** : désactive l’optimisation.<br/>**Réduire la taille** : optimise la taille.<br/>**Augmenter la vitesse** : optimise la vitesse.<br/>**Optimisation complète** : optimisations coûteuses.<br/>
Alias strict | Les règles d’alias les plus strictes sont utilisées.  Un objet d’un type donné n’est jamais considéré comme résidant à la même adresse qu’un objet d’un autre type.
Dérouler les boucles | Déroule les boucles pour rendre l’application plus rapide en réduisant le nombre de branches exécutées au prix d’un code de plus grande taille.
Optimisation durant l’édition de liens | Active les optimisations inter-procédurales en permettant à l’optimiseur d’accéder aux fichiers objets dans votre application.
Omettre le pointeur de frame | Empêche la création des pointeurs de frame sur la pile des appels.
Aucun bloc commun | Alloue des variables globales, même non initialisées, dans la section de données du fichier objet, au lieu de les générer en tant que blocs communs

## <a name="preprocessor"></a>Préprocesseur

Property | Description | Options
--- | ---| ---
Définitions de préprocesseur | Définit des symboles de prétraitement pour votre fichier source. (-D)
Annuler la définition de définitions de préprocesseur | Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur.  (-U [macro])
Annulation de la définition de toutes les définitions du préprocesseur | Annule la définition de toutes les valeurs de préprocesseur précédemment définies.  (-undef)
Affichage des fichiers Include | Affiche la liste des fichiers include avec les résultats de la compilation.  (-H)

## <a name="code-generation"></a>Génération de code

Property | Description | Options
--- | ---| ---
PIC (Position Independent Code) | Génère le code PIC (Position Independent Code) à utiliser dans une bibliothèque partagée.
Les statiques sont thread-safe | Génère du code supplémentaire qui permet d’utiliser les routines spécifiées dans l’ABI C++ pour l’initialisation thread-safe des statiques locales. | **Non** : désactive les statiques thread-safe.<br/>**Oui** : active les statiques thread-safe.<br/>
Optimisation à virgule flottante | Active les optimisations à virgule flottante en assouplissant la conformité à la norme IEEE-754.
Méthodes inline masquées | Une fois activées, les copies hors ligne des méthodes inline sont déclarées 'private extern'.
Symboles masqués par défaut | Tous les symboles sont déclarés 'private extern', sauf s’ils sont explicitement marqués pour être exportés à l’aide de la macro '__attribute'.
Activer les exceptions C++ | Spécifie le modèle de gestion des exceptions à utiliser par le compilateur. | **Non** : désactive la gestion des exceptions.<br/>**Oui** : active la gestion des exceptions.<br/>

## <a name="language"></a>Langue

Property | Description | Options
--- | ---| ---
Activer les informations de type au moment de l’exécution | Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).     (frtti, fno-rtti)
Norme du langage C | Détermine la norme du langage C. | **Default**<br/>**C89** : norme du langage C89.<br/>**C99** : norme du langage C99.<br/>**C11** : norme du langage C11.<br/>**C99 (Dialecte GNU)**  : norme du langage C99 (Dialecte GNU).<br/>**C11 (Dialecte GNU)**  : norme du langage C11 (Dialecte GNU).<br/>
Norme du langage C++ | Détermine la norme du langage C++. | **Default**<br/>**C++03** : norme du langage C++03.<br/>**C++11** : norme du langage C++11.<br/>**C++14** : norme du langage C++14.<br/>**C++03 (Dialecte GNU)**  : norme du langage C++03 (Dialecte GNU).<br/>**C++11 (Dialecte GNU)**  : norme du langage C++11 (Dialecte GNU).<br/>**C++14 (Dialecte GNU)**  : norme du langage C++14 (Dialecte GNU).<br/>

## <a name="advanced"></a>Avancé

Property | Description | Options
--- | ---| ---
Compiler en | Permet de sélectionner l’option de langage de compilation pour les fichiers .c et .cpp.  'Default' effectue la détection d’après l’extension (.c ou .cpp). (-x c, -x c++) | **Par défaut** : option par défaut.<br/>**Compiler en code C** : compile en code C.<br/>**Compiler en code C++**  : compile en code C++.<br/>
Fichiers Include forcés | Un ou plusieurs fichiers Include forcés. (-include [name])

## <a name="additional-options"></a>Options supplémentaires 
