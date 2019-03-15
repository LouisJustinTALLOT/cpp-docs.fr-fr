---
title: Fichiers d'entrée LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808129"
---
# <a name="lib-input-files"></a>Fichiers d'entrée LIB

Les fichiers d’entrée attendus par LIB varient selon le mode dans lequel il est utilisé, comme indiqué dans le tableau suivant.

|Mode|Entrée|
|----------|-----------|
|Par défaut (création ou modification d’une bibliothèque)|Objet (.obj) fichiers, COFF bibliothèques (.lib), fichiers objet (.obj) de Format OMF (Object Model) 32 bits|
|Extraction d’un membre avec /EXTRACT|Bibliothèque COFF (.lib)|
|Création d’une exportation de fichier et de bibliothèque avec /DEF d’importation|Fichier de définition de module (.def), fichiers objets (.obj), COFF bibliothèques (.lib), les fichiers objet (.obj) OMF 32 bits|

> [!NOTE]
>  Bibliothèques OMF créés par la version 16 bits de LIB ne peut pas être utilisés en tant qu’entrée vers la version 32 bits de LIB.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de LIB](overview-of-lib.md)
