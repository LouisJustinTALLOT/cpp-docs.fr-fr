---
description: 'En savoir plus sur : __svm_invlpga'
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: dc976f535381fcfdfec0da5c1a280c4df281c114
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314748"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Spécifique à Microsoft**

Invalide l’entrée de mappage d’adresse dans la mémoire tampon de recherche de la traduction de l’ordinateur. Les paramètres spécifient l’adresse virtuelle et l’identificateur de l’espace d’adressage de la page à invalider.

## <a name="syntax"></a>Syntaxe

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>Paramètres

*Vaddr*\
dans Adresse virtuelle de la page à invalider.

*as_id*\
dans Identificateur de l’espace d’adressage (ASID) de la page à invalider.

## <a name="remarks"></a>Notes

La fonction `__svm_invlpga` est équivalente à l’instruction machine `INVLPGA` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « AMD64 architecture Programmer’s Manual volume 2 : System Programming », numéro de document 24593, Revision 3,11, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
