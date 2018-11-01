---
title: Erreur irrécupérable C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: bb1d9af10084d6b3e75325450c7f13ea1683ee2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661216"
---
# <a name="fatal-error-c1128"></a>Erreur irrécupérable C1128

nombre de sections a dépassé la limite du format de fichier objet : compilez avec /bigobj

Un fichier .obj a dépassé le nombre de sections autorisé, une limitation du format de fichier objet COFF.

Limitation du nombre de cette section peut être le résultat de l’utilisation de [/Gy](../../build/reference/gy-enable-function-level-linking.md) et une version debug ; **/Gy** , les fonctions passent dans leurs propres sections COMDAT. Dans une version debug, il existe une section d’informations de débogage pour chaque fonction COMDAT.

C1128 peut également être provoquée lorsqu’il y a trop de fonctions inline.

Pour corriger cette erreur, divisez votre fichier source en plusieurs fichiers de code source, compilez sans **/Gy**, ou compilez avec [/bigobj (augmenter le nombre de Sections dans. Fichier obj)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Si vous ne compilez pas avec **/Gy**, vous devez spécifier les optimisations individuellement, dans la mesure où **/O2** et **/O1** impliquent toutes les deux **/Gy**.

Dans la mesure du possible, compilez sans informations de débogage.

Vous devrez peut-être également avoir des instanciations spécifiques de modèles dans les fichiers de code source distinct, plutôt que de laisser le compilateur de les émettre.

Lors du portage du code, C1128 probablement apparaît en premier lorsque vous utilisez le x64 compilateur et beaucoup plus tard avec la x86 compilateur. x64 aura au moins 4 sections associées à chaque fonction compilée avec **/Gy** ou inline à partir de modèles ou d’une classe inline : code, pdata et les informations de débogage et éventuellement xdata.  X86 ne comprend pas pdata.