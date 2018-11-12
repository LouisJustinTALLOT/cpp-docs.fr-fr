---
title: Redistribution de contrôles ActiveX Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 6c1f75665d43d927e21a1fd7d365e1bde46c57a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551396"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribution de contrôles ActiveX Visual C++

Visual C++ 6.0 fournit des contrôles ActiveX que vous pouvez utiliser dans des applications que vous redistribuez ensuite. Ces contrôles ne sont plus inclus dans Visual C++. Conformément aux contrats de licence de Visual C++ 6.0, vous pouvez redistribuer ces contrôles avec les applications développées en Visual C++.

> [!NOTE]
>  Visual C++ 6.0 n’est plus pris en charge par Microsoft.

Pour obtenir une liste des contrôles ActiveX redistribuables Visual C++ 6.0, consultez Common\Redist\Redist.txt sur le disque 1 du CD-ROM du produit Visual C++ 6.0.

Quand vous distribuez des applications, vous devez installer et inscrire le fichier .ocx du contrôle ActiveX (à l’aide de Regsvr32.exe). Par ailleurs, vous devez vérifier que l’ordinateur cible dispose des versions actuelles des fichiers système suivants (un astérisque indique que le fichier doit être inscrit) :

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

Si ces DLL ne sont pas disponibles sur le système cible, vous devez les mettre à jour selon le mécanisme recommandé pour la mise à jour du système d’exploitation correspondant. Vous pouvez télécharger les versions les plus récentes des Service Packs pour les systèmes d’exploitation Windows depuis [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com).

Quand vous utilisez un contrôle ActiveX qui établit une connexion à une base de données, vous devez également répliquer le nom de la source de données sur l’ordinateur cible. Vous pouvez effectuer cette opération par programmation à l’aide de fonctions telles que `ConfigDSN`.

Certains contrôles ActiveX redistribuables ont des dépendances supplémentaires. Pour chaque fichier .ocx du dossier Os\System situé sur le CD-ROM du produit Visual C++ 6.0, il existe également un fichier .dep. Pour chaque fichier .ocx que vous voulez redistribuer, recherchez une ou plusieurs entrées USES dans le fichier .dep correspondant. Si un fichier est répertorié, vous devez vous assurer qu’il se trouve sur l’ordinateur cible. Toutes les DLL prenant directement en charge un fichier .ocx doivent être inscrites. (Pour que l’exécution de Regsvr32.exe réussisse, l’ordinateur cible doit contenir au préalable l’ensemble des DLL chargées statiquement par le contrôle.) De plus, si une DLL répertoriée en tant que dépendance a également un fichier .dep dans le dossier Os\System situé sur le CD-ROM de Visual C++ 6.0, vous devez également rechercher les entrées USES dans ce fichier .dep.

## <a name="see-also"></a>Voir aussi

[Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md)