---
description: 'En savoir plus sur : __svm_skinit'
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: dd35566664a6bff4a57ea986fc99ffcd731c79e2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206264"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Spécifique à Microsoft**

Lance le chargement de logiciels sécurisés et vérifiés, tels qu’un moniteur d’ordinateur virtuel.

## <a name="syntax"></a>Syntaxe

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>Paramètres

*block_address*\
Adresse physique 32 bits d’un bloc de chargement sécurisé à 64 octets (SLB).

## <a name="remarks"></a>Notes

La fonction `__svm_skinit` est équivalente à l’instruction machine `SKINIT` . Cette fonction fait partie d’un système de sécurité qui utilise le processeur et un Module de plateforme sécurisée (TPM) (TPM), pour vérifier et charger un logiciel approuvé, appelé *noyau de sécurité* (SK). Un moniteur d’ordinateur virtuel est un exemple de noyau de sécurité. Le système de sécurité vérifie les composants de programme chargés pendant le processus d’initialisation. Il protège les composants contre la falsification par des interruptions, l’accès des appareils ou un autre programme si l’ordinateur est un multiprocesseur.

Le paramètre *block_address* spécifie l’adresse physique d’un bloc de mémoire 64 Ko appelé *bloc de chargeur sécurisé* (SLB). Le SLB contient un programme appelé *chargeur sécurisé*. Il établit l’environnement d’exploitation de l’ordinateur, puis charge le noyau de sécurité.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez « Configuration manuelle du volume 2 : programmation du système par le programmeur d’architecture AMD64 » sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_skinit`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
