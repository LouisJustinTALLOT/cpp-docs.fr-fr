---
title: Fichiers projet et solution
ms.date: 05/06/2019
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
ms.openlocfilehash: 73d1733afde9dd62081d071df025c76bba5729d1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492656"
---
# <a name="project-and-solution-files"></a>Fichiers projet et solution

Les fichiers suivants sont créés en même temps que vous créez un projet dans Visual Studio. Ils servent à gérer les fichiers projet de la solution.

|Nom de fichier|Emplacement du répertoire|Emplacement dans l'Explorateur de solutions|Description|
|--------------|------------------------|--------------------------------|-----------------|
|*Solname*.sln|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier *solution*. Permet d'organiser tous les éléments d'un ou plusieurs projets dans une même solution.|
|*Projname*.suo|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier *d’options de solution*. Permet de stocker les personnalisations de la solution pour que chaque fois que vous ouvrez un projet ou un fichier de la solution, il ait l'apparence et le comportement que vous attendez.|
|*Projname*.vcxproj|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier *projet*. Permet de stocker les informations propres à chaque projet. (Dans les versions antérieures, ce fichier s’appelait *Projname*.vcproj ou *Projname*.dsp.) Pour obtenir un exemple de fichier projet C++ (.vcxproj), consultez [Fichiers projet](project-files.md).|
|*Nomproj*.vcxitems|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier *projet d’éléments partagés*. Le projet n’est pas généré.  À la place, le projet peut être référencé par un autre projet C++ et ses fichiers font partie du processus de génération du projet de référence. C’est un moyen de partager le code commun avec les projets C++ multiplateformes.|
|*Projname*.sdf|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier de *base de données de navigation*. Prend en charge les fonctionnalités de navigation comme **Atteindre la définition**, **Rechercher toutes les références** et **Affichage de classes**. Il est généré en analysant les fichiers d'en-tête.|
|*Projname*.vcxproj.filters|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier de *filtres*. Permet de spécifier l'emplacement d'un fichier ajouté à la solution. Par exemple, un fichier .h est placé dans le nœud **Fichiers d’en-tête**.|
|*Projname*.vcxproj.user|*Projname*|Non affiché dans l'Explorateur de solutions|Fichier *utilisateur de migration*. Suite à la migration d'un projet à partir de Visual Studio 2008, ce fichier contient des informations qui ont été converties à partir d'un fichier .vsprops.|
|*Projname*.idl|*Projname*|source|(Propre au projet) Contient le code source IDL (Interface Description Langage) d'une bibliothèque de types de contrôles. Visual C++ se sert de ce fichier pour générer une bibliothèque de types. La bibliothèque générée expose l'interface du contrôle aux autres clients Automation. Pour plus d’informations, consultez [Fichier IDL (Interface Definition Language)](/windows/win32/Rpc/the-interface-definition-language-idl-file) dans le SDK Windows.|
|Readme.txt|*Projname*|Projet|Fichier *Lisez moi*. Généré par l'Assistant Application, il décrit les fichiers contenus dans un projet.|

## <a name="see-also"></a>Voir aussi

[Types de fichiers créés pour les projets Visual Studio C++](file-types-created-for-visual-cpp-projects.md)
