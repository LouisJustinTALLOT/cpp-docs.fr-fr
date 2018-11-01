---
title: Fichiers affectés par la ressource de modification (C++)
ms.date: 06/18/2018
helpviewer_keywords:
- resource editing
- resources [C++], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
ms.openlocfilehash: 891794f42f3df1ab23d64c253ab4df8291e3ddcf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663298"
---
# <a name="files-affected-by-resource-editing-c"></a>Fichiers affectés par la ressource de modification (C++)

L'environnement Visual Studio fonctionne avec les fichiers indiqués dans le tableau ci-dessous pendant votre session de modification des ressources.

|Nom de fichier|Description|
|---------------|-----------------|
|Resource.h|Fichier d'en-tête généré par l'environnement de développement. Il contient les définitions de symbole. (Inclure ce fichier dans le contrôle de code source.)|
|Filename.aps|Version binaire du fichier de script de ressources actif. Ce fichier est utilisé pour le chargement rapide.<br /><br /> Les éditeurs de ressources ne lisent pas directement les fichiers .rc ou resource.h. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md). (En règle générale, vous devez inclure pas du fichier .aps dans le contrôle de code source.)|
|.rc|Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement. (Inclure ce fichier dans le contrôle de code source.)|

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)