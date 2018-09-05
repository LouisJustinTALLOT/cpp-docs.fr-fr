---
title: . Fichiers obj en tant qu’entrée de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd1fbd635b1d3d3a5f9963edaa9f22e22472dad1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691749"
---
# <a name="obj-files-as-linker-input"></a>Fichiers .obj en tant qu'entrée de l'Éditeur de liens

L’outil Éditeur de liens (lien. (EXE) accepte des fichiers .obj en fichier de Format COFF (Common Object).

## <a name="remarks"></a>Notes

Microsoft fournit une description complète du format de fichier objet commun. Pour plus d’informations, consultez [Format PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Prise en charge Unicode

À compter de Visual Studio 2005, le compilateur Microsoft Visual C++ prend en charge les caractères Unicode dans les identificateurs, comme défini par la norme ISO/IEC normes C et C++. Les versions précédentes du compilateur pris en charge uniquement des caractères ASCII dans les identificateurs. Pour prendre en charge Unicode dans les noms de fonctions, des classes et des variables statiques, le compilateur et l’éditeur de liens utilisent l’encodage Unicode UTF-8 pour les symboles COFF dans les fichiers .obj. L’encodage UTF-8 est la compatibilité ascendante avec l’encodage ASCII utilisé par les versions antérieures de Visual Studio.

Pour plus d’informations sur le compilateur et l’éditeur de liens, consultez [prise en charge Unicode dans le compilateur et l’éditeur de liens](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Pour plus d’informations sur la norme Unicode, consultez le [Unicode](http://www.unicode.org/) organisation.

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)  
[Options de l’éditeur de liens](../../build/reference/linker-options.md)  
[Prise en charge pour Unicode](../../text/support-for-unicode.md)  
[Prise en charge Unicode dans le compilateur et l’éditeur de liens](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Norme Unicode](http://www.unicode.org/)  
[Format PE](/windows/desktop/Debug/pe-format)  
