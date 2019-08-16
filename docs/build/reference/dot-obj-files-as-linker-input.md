---
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
ms.openlocfilehash: 3e02ccc09ae8c9c2f3df88bc1767ff0188baa1f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492936"
---
# <a name="obj-files-as-linker-input"></a>Fichiers .obj en tant qu'entrée de l'Éditeur de liens

Outil Éditeur de liens (LINK. EXE) accepte les fichiers. obj au format COFF (Common Object File Format).

## <a name="remarks"></a>Notes

Microsoft fournit une description complète du format de fichier objet commun. Pour plus d’informations, consultez [format PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Prise en charge Unicode

À compter de Visual Studio 2005, le compilateur Microsoft MSVC prend en charge les caractères Unicode dans les identificateurs, comme défini par C++ les normes ISO/IEC C et. Les versions précédentes du compilateur ne prenait en charge que les caractères ASCII dans les identificateurs. Pour prendre en charge Unicode dans les noms des fonctions, des classes et des statiques, le compilateur et l’éditeur de liens utilisent l’encodage Unicode UTF-8 pour les symboles COFF dans les fichiers. obj. L’encodage UTF-8 est à compatibilité ascendante avec l’encodage ASCII utilisé par les versions antérieures de Visual Studio.

Pour plus d’informations sur le compilateur et l’éditeur de liens, consultez [prise en charge d’Unicode dans le compilateur et l’éditeur de liens](unicode-support-in-the-compiler-and-linker.md). Pour plus d’informations sur la norme Unicode, consultez l’organisation [Unicode](https://www.unicode.org/) .

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[Prise en charge pour Unicode](../../text/support-for-unicode.md)<br/>
[Prise en charge Unicode dans le compilateur et l’éditeur de liens](unicode-support-in-the-compiler-and-linker.md)<br/>
[Norme Unicode](https://www.unicode.org/)<br/>
[Format PE](/windows/win32/Debug/pe-format)
