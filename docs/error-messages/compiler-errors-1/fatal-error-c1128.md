---
title: Erreur irrécupérable C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203629"
---
# <a name="fatal-error-c1128"></a>Erreur irrécupérable C1128

le nombre de sections a dépassé la limite du format de fichier objet : compilez avec/bigobj

Un fichier. obj a dépassé le nombre de sections autorisées, une limitation au format de fichier objet COFF.

L’atteinte de cette limitation de section peut être le résultat de l’utilisation de [/Gy](../../build/reference/gy-enable-function-level-linking.md) et d’une version Debug. **/Gy** fait en sorte que les fonctions entrent dans leurs propres sections COMDAT. Dans une version Debug, il existe une section d’informations de débogage pour chaque fonction COMDAT.

C1128 peut également être dû à un trop grand nombre de fonctions inline.

Pour corriger cette erreur, divisez votre fichier source en plusieurs fichiers de code source, compilez sans **/Gy**, ou compilez avec [/bigobj (augmenter le nombre de sections dans. Fichier OBJ)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Si vous ne compilez pas avec **/Gy**, vous devez spécifier les optimisations individuellement, car **/O2** et **/O1** impliquent **/Gy**.

Si possible, compilez sans informations de débogage.

Vous devrez peut-être également avoir des instanciations de modèles spécifiques dans des fichiers de code source distincts, plutôt que de faire en sorte que le compilateur les émette.

Lors du Portage du code, C1128 apparaîtra probablement en premier lorsque vous utiliserez le compilateur x64, et plus tard avec le compilateur x86. x64 aura au moins 4 sections associées à chaque fonction dans le calcul de la fonction **/Gy** ou Inline à partir de modèles ou de Class-inline : code, pData, informations de débogage et éventuellement XData.  X86 n’aura pas pData.
