---
title: Énumération BufferCommand
description: 'Décrit l’énumération BufferCommand, qui est utilisée pour travailler avec des fichiers de mémoire via CMemFile :: GetBufferPtr ()'
ms.date: 07/23/2020
f1_keywords:
- afx/buffercommand
helpviewer_keywords:
- buffercommand enumeration [MFC]
ms.openlocfilehash: f2f553df56fadd99b65b04cce9a97917425ed70b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246103"
---
# <a name="buffercommand-enumeration"></a>Énumération BufferCommand

Utilisé par [CMemFile :: GetBufferPtr](cmemfile-class.md#getbufferptr) pour déterminer l’action à effectuer sur la mémoire tampon de mémoire sauvegardée.

## <a name="syntax"></a>Syntaxe

``` cpp
public enum BufferCommand
{
   bufferRead,
   bufferWrite,
   bufferCommit,
   bufferCheck
};
```

## <a name="members"></a>Membres

|Nom|Description|
|-|-|
| `bufferRead` | Lisez le tampon mémoire sauvegardée dans les fichiers. |
| `bufferWrite` | Écrire dans la mémoire tampon de mémoire sauvegardée. |
| `bufferCommit` | Avance la position actuelle dans la mémoire tampon de mémoire stockée à la fin de la mémoire tampon validée. |
| `bufferCheck` | Déterminez si la taille du tampon de mémoire stocké dans les fichiers peut croître. |

## <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)
