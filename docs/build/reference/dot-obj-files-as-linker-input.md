---
description: En savoir plus sur :. Fichiers obj en tant qu’entrée dans l’éditeur de liens
title: Fichiers .obj en tant qu'entrée de l'Éditeur de liens
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 33b4a9d9a23854766100d0b023713f7ecbc71e32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192718"
---
# <a name="obj-files-as-linker-input"></a>Fichiers .obj en tant qu'entrée de l'Éditeur de liens

L’outil Éditeur de liens (LINK.EXE) accepte les fichiers. obj au format COFF (Common Object File Format).

## <a name="remarks"></a>Notes

Microsoft fournit une description complète du format de fichier objet commun. Pour plus d’informations, consultez [format PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Prise en charge d’Unicode

À compter de Visual Studio 2005, le compilateur Microsoft MSVC prend en charge les caractères Unicode dans les identificateurs, comme défini par les normes ISO/IEC C et C++. Les versions précédentes du compilateur ne prenait en charge que les caractères ASCII dans les identificateurs. Pour prendre en charge Unicode dans les noms des fonctions, des classes et des statiques, le compilateur et l’éditeur de liens utilisent l’encodage Unicode UTF-8 pour les symboles COFF dans les fichiers. obj. L’encodage UTF-8 est à compatibilité ascendante avec l’encodage ASCII utilisé par les versions antérieures de Visual Studio.

Pour plus d’informations sur le compilateur et l’éditeur de liens, consultez [prise en charge d’Unicode dans le compilateur et l’éditeur de liens](unicode-support-in-the-compiler-and-linker.md). Pour plus d’informations sur la norme Unicode, consultez l’organisation [Unicode](https://home.unicode.org/) .

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée de lien](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Prise en charge pour Unicode](../../text/support-for-unicode.md)<br/>
[Prise en charge Unicode dans le compilateur et l’éditeur de liens](unicode-support-in-the-compiler-and-linker.md)<br/>
[Norme Unicode](https://home.unicode.org/)<br/>
[Format PE](/windows/win32/Debug/pe-format)
