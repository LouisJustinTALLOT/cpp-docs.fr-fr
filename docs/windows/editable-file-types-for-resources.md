---
title: Types de fichier modifiables pour les ressources (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: c40f9204-f2f2-400b-9f53-53b7bf291356
ms.openlocfilehash: 9f688c144a3453c2de849b36f34f6a465e3dfeae
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905717"
---
# <a name="editable-file-types-for-resources-c"></a>Types de fichier modifiables pour les ressources (C++)

Vous pouvez ouvrir les types de fichier suivants, et modifier les ressources qu'ils contiennent.

|Nom de fichier|Description|
|---------------|-----------------|
|.rc|Fichiers de script de ressources.|
|.rct|Fichiers modèles de ressources.|
|.res|Fichiers de ressources.|
|.resx|Fichiers de ressources managées.|
|.exe|Fichiers exécutables.|
|.dll|Fichiers bibliothèques de liens dynamiques.|
|.bmp, .ico, .dib et .cur|Fichiers bitmap, icône, barre d'outils et curseur.|

## <a name="files-affected-by-resource-editing"></a>Fichiers affectés par la modification de la ressource

L'environnement Visual Studio fonctionne avec les fichiers indiqués dans le tableau ci-dessous pendant votre session de modification des ressources.

|Nom de fichier|Description|
|---------------|-----------------|
|Resource.h|Fichier d'en-tête généré par l'environnement de développement. Il contient les définitions de symbole. (Inclure ce fichier dans le contrôle de code source.)|
|Filename.aps|Version binaire du fichier de script de ressources actif. Ce fichier est utilisé pour le chargement rapide.<br /><br /> Les éditeurs de ressources ne lisent pas directement les fichiers .rc ou resource.h. Le compilateur de ressources les compile en fichiers .aps, qui sont consommés par les éditeurs de ressources. Ce fichier est une étape de compilation, qui stocke uniquement les données symboliques. Comme pour un processus de compilation normal, les informations non symboliques (par exemple les commentaires) sont ignorées durant le processus de compilation. Chaque fois que le fichier .aps n'est plus synchronisé au fichier .rc, le fichier .rc est régénéré (par exemple, quand vous effectuez un enregistrement, l'éditeur de ressources remplace les fichiers .rc et resource.h). Les changements apportés aux ressources sont conservés dans le fichier .rc, mais les commentaires disparaissent une fois le fichier .rc remplacé. Pour plus d’informations sur la façon de conserver les commentaires, consultez [inclusion des ressources au moment de la compilation](../windows/how-to-include-resources-at-compile-time.md). (En règle générale, vous devez inclure pas du fichier .aps dans le contrôle de code source.)|
|.rc|Fichier de script de ressources qui contient le script des ressources de votre projet actif. Ce fichier est remplacé par le fichier .aps à chaque enregistrement. (Inclure ce fichier dans le contrôle de code source.)|

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Fichiers de ressources](../windows/resource-files-visual-studio.md)