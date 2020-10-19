---
title: C/C++, propriétés (Linux C++)
ms.date: 10/14/2020
description: Décrit les options de compilation Linux sur la page de propriétés de Visual Studio C/C++
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: 0840327b30d94b4845adef7788fd73f4e797775f
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176236"
---
# <a name="cc-properties-linux-c"></a>C/C++, propriétés (Linux C++)

::: moniker range="vs-2015"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Général

| Propriété | Description | Choices |
|--|--|--|
| Autres répertoires Include | Spécifie un ou plusieurs répertoires à ajouter au chemin include. Utilisez des points-virgules pour séparer plusieurs répertoires. (-I\[path]). |
| Format des informations de débogage | Indique le type d'informations de débogage générées par le compilateur. | **Aucune** : ne génère aucune information de débogage ; la compilation peut donc être plus rapide.<br/>**Informations de débogage minimales** : génère des informations de débogage minimales.<br/>**Informations de débogage complètes (DWARF2)** : générez des informations de débogage DWARF2.<br/> |
| Nom de fichier objet | Spécifie un nom de substitution pour le nom de fichier objet par défaut. Il peut s’agir d’un nom de fichier ou de répertoire. (-o [name]). |
| Niveau d’avertissement | Sélectionne la rigueur avec laquelle le compilateur doit traiter les erreurs de code.  Ajoutez d’autres indicateurs directement dans les **Options supplémentaires**. (/w, /Weverything). | **Désactiver tous les avertissements** : désactive tous les avertissements du compilateur.<br/>**Activer tous les avertissements** : active tous les avertissements, dont ceux qui sont désactivés par défaut.<br/> |
| Considérer les avertissements comme des erreurs | Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable d’utiliser /Werror dans toutes les compilations. Résolvez tous les avertissements pour avoir le moins de défauts de code difficiles à détecter possible. |
| Avertissements supplémentaires C | Définit un ensemble de messages d’avertissement supplémentaires. |
| Avertissements supplémentaires C++ | Définit un ensemble de messages d’avertissement supplémentaires. |
| Activer le mode détaillé | Quand le mode détaillé est activé, affiche des informations complémentaires facilitant le diagnostic de la build. |
| Compilateur C | Spécifie le programme à appeler durant la compilation de fichiers sources C, ou le chemin du compilateur C sur le système distant. |
| Compilateur C++ | Spécifie le programme à appeler durant la compilation de fichiers sources C++, ou le chemin du compilateur C++ sur le système distant. |
| Délai d’attente de la compilation | Délai d’attente de la compilation distante en millisecondes. |
| Copier les fichiers objets | Indique s’il faut copier les fichiers objets compilés du système distant sur la machine locale. |
| Nombre maximal de travaux de compilation parallèles | Nombre de processus à créer en parallèle pendant la compilation. La valeur par défaut est 1. Si vous utilisez le sous-système Windows pour Linux (WSL) version 1, la limite est de 64. |
| Valider l’architecture | Spécifiez s’il faut vérifier si la plateforme ciblée par le projet correspond au système distant.|
| Activer le désinfectant d’adresse | Compilez le programme avec l’adresse assainir, qui est un détecteur d’erreurs de mémoire rapide qui peut détecter les problèmes de mémoire d’exécution tels que l’utilisation de-après-gratuit, et effectuer des vérifications hors limites.|

## <a name="optimization"></a>Optimization

| Propriété | Description | Choices |
|--|--|--|
| Optimization | Indique le niveau d’optimisation pour l’application. | **Personnalisé** : optimisation personnalisée.<br/>**Désactivé** : désactive l’optimisation.<br/>**Réduire la taille** : optimise la taille.<br/>**Augmenter la vitesse** : optimise la vitesse.<br/>**Optimisation complète** : optimisations coûteuses. |
| Alias strict | Les règles d’alias les plus strictes sont utilisées.  Un objet d’un type donné n’est jamais considéré comme ayant la même adresse qu’un objet d’un autre type. |
| Dérouler les boucles | Déroule les boucles pour rendre l’application plus rapide en réduisant le nombre de branches exécutées, au prix d’un code de plus grande taille. |
| Optimisation durant l’édition de liens | Active les optimisations inter-procédurales en permettant à l’optimiseur d’accéder aux fichiers objets dans votre application. |
| Omettre le pointeur de frame | Empêche la création des pointeurs de frame sur la pile des appels. |
| Aucun bloc commun | Alloue des variables globales, même non initialisées, dans la section de données du fichier objet, au lieu de les générer en tant que blocs communs. |

## <a name="preprocessor"></a>Préprocesseur

| Propriété | Description |
|--|--|
| Définitions de préprocesseur | Définit les symboles de prétraitement pour votre fichier source. (-D) |
| Annuler la définition de définitions de préprocesseur | Spécifie l’annulation de la définition d’une ou de plusieurs définitions du préprocesseur.  (-U \[macro]) |
| Annulation de la définition de toutes les définitions du préprocesseur | Annule la définition de toutes les valeurs de préprocesseur précédemment définies.  (-undef) |
| Affichage des fichiers Include | Affiche la liste des fichiers include avec les résultats de la compilation.  (-H) |

## <a name="code-generation"></a>Génération de code

| Propriété | Description | Choices |
|--|--|--|
| PIC (Position Independent Code) | Génère le code PIC (Position Independent Code) à utiliser dans une bibliothèque partagée. |
| Les statiques sont thread-safe | Génère du code supplémentaire qui permet d’utiliser les routines spécifiées dans l’ABI C++ pour l’initialisation thread-safe des statiques locales. | **Non** : désactive les statiques thread-safe.<br/>**Oui** : active les statiques thread-safe. |
| Optimisation à virgule flottante | Active les optimisations à virgule flottante en assouplissant la conformité à la norme IEEE-754. |
| Méthodes inline masquées | Une fois activées, les copies hors ligne des méthodes inline sont déclarées `private extern`. |
| Symboles masqués par défaut | Tous les symboles sont déclarés `private extern` sauf s’ils sont explicitement marqués pour l’exportation à l’aide de la macro `__attribute`. |
| Activer les exceptions C++ | Spécifie le modèle de gestion des exceptions utilisé par le compilateur. | **Non** : désactive la gestion des exceptions.<br/>**Oui** : active la gestion des exceptions. |

## <a name="language"></a>Langage

| Propriété | Description | Choices |
|--|--|--|
| Activer les informations de type au moment de l’exécution | Ajoute le code permettant de vérifier les types d’objet C++ à l’exécution (informations de type au moment de l’exécution).     (frtti, fno-rtti) |
| Norme du langage C | Détermine la norme du langage C. | **Par défaut**<br/>**C89** : norme du langage C89.<br/>**C99** : norme du langage C99.<br/>**C11** : norme du langage C11.<br/>**C99 (Dialecte GNU)**  : norme du langage C99 (Dialecte GNU).<br/>**C11 (dialecte GNU)** -norme du langage C11 (dialecte GNU). |
| Norme du langage C++ | Détermine la norme du langage C++. | **Par défaut**<br/>**C++03** : norme du langage C++03.<br/>**C++ 11** -norme du langage c++ 11.<br/>**C++14** : norme du langage C++14.<br/>**C++03 (Dialecte GNU)**  : norme du langage C++03 (Dialecte GNU).<br/>**C++11 (Dialecte GNU)**  : norme du langage C++11 (Dialecte GNU).<br/>**C++14 (Dialecte GNU)**  : norme du langage C++14 (Dialecte GNU). |

## <a name="advanced"></a>Avancé

| Propriété | Description | Choices |
|--|--|--|
| Compiler en | Sélectionne l’option de langage de compilation pour les fichiers .c et .cpp. (-x c, -x c++) | **Par défaut** : effectue la détection d’après l’extension (.c ou .cpp).<br/>**Compilez en code c** -compile en code c.<br/>**Compiler en code c++** -compiler en code c++. |
| Fichiers Include forcés | Spécifie un ou plusieurs fichiers Include forcés (-include \[name]). |

::: moniker-end
