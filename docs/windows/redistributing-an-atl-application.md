---
description: 'En savoir plus sur : redistribution d’une application ATL'
title: Redistribution d'une application ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
ms.openlocfilehash: 58021416eb7f258e1d436ff099ebf9c647dfc0bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179952"
---
# <a name="redistributing-an-atl-application"></a>Redistribution d'une application ATL

À compter de Visual Studio 2012, la bibliothèque ATL (Active Template Library) est une bibliothèque à en-tête uniquement. Les projets ATL ne possèdent pas d'option Lien dynamique vers ATL. Aucun composant redistribuable de bibliothèque ATL n'est requis.

Si vous redistribuez une application ATL exécutable, vous devez inscrire le fichier .exe (et tous les contrôles qu'il contient) en émettant la commande suivante :

```
filename /regserver
```

où `filename` est le nom du fichier exécutable.

Dans Visual Studio 2010, un projet ATL peut être généré pour une configuration MinDependency ou MinSize. Une configuration MinDependency est le résultat que vous obtenez quand vous affectez à la propriété **Utilisation des ATL** la valeur **Lien statique vers ATL** dans la page de propriétés **Général** et quand vous affectez à la propriété **Bibliothèque Runtime** la valeur **Multithread (/MT)** dans la page de propriétés **Génération de code** (dossier C/C++).

Une configuration MinSize est le résultat que vous obtenez quand vous affectez à la propriété **Utilisation des ATL** la valeur **Lien dynamique vers ATL** dans la page de propriétés **Général** ou quand vous affectez à la propriété **Bibliothèque Runtime** la valeur **DLL multithread (/MD)** dans la page de propriétés **Génération de code** (dossier C/C++).

MinSize réduit autant que possible le fichier de sortie, mais nécessite que les fichiers ATL100.dll et Msvcr100.dll (si vous avez sélectionné l’option **DLL multithread (/MD)**) se trouvent sur l’ordinateur cible. Le fichier ATL100.dll doit être inscrit sur l'ordinateur cible pour garantir la présence de toutes les fonctionnalités ATL seront présentes. ATL100.dll contient des exports ANSI et Unicode.

Si vous générez votre projet de modèles ATL ou OLE DB pour une cible MinDependency, il est inutile d'installer et d'inscrire ATL100.dll sur l'ordinateur cible, bien que vous puissiez obtenir une image de programme plus grande.

Si vous redistribuez une application ATL exécutable, vous devez inscrire le fichier .exe (et tous les contrôles qu'il contient) en émettant la commande suivante :

```
filename /regserver
```

où `filename` est le nom du fichier exécutable.

## <a name="see-also"></a>Voir aussi

[Redistribution des fichiers Visual C++](redistributing-visual-cpp-files.md)
