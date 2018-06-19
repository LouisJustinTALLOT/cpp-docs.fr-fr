---
title: Utilisation des registres | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c77469a8cef03827101f4bf367c00a3bb440820
ms.sourcegitcommit: 4fc6869067d533b175207befd2dc60346afee285
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225217"
---
# <a name="register-usage"></a>Utilisation des registres

L’architecture fournit pour 16 registres généraux (ci-après dénommés registres d’entiers) ainsi que 16 registres XMM/YMM de x64 inscrit disponibles pour une utilisation à virgule flottante. Les registres volatils sont des registres de travail censés être détruits après un appel. Les registres non volatils doivent conserver leurs valeurs tout au long d'un appel de fonction et être enregistrés par l'appelé s'il les utilise.

## <a name="register-volatility-and-preservation"></a>Inscrire la volatilité et la préservation de

Le tableau suivant explique comment chaque registre est utilisé dans les appels de fonction :

||||
|-|-|-|
|Registre|État|Utilisez|
|RAX|Volatil|Registre des valeurs de retour|
|RCX|Volatil|Premier argument entier|
|RDX|Volatil|Deuxième argument entier|
|R8|Volatil|Troisième argument entier|
|R9|Volatil|Quatrième argument entier|
|R10:R11|Volatil|Doit être conservé si nécessaire par l'appelant ; utilisé dans les instructions syscall/sysret|
|R12:R15|Non volatil|Doit être conservé par l'appelé|
|RDI|Non volatil|Doit être conservé par l'appelé|
|RSI|Non volatil|Doit être conservé par l'appelé|
|RBX|Non volatil|Doit être conservé par l'appelé|
|RBP|Non volatil|Peut être utilisé comme pointeur de frame ; doit être conservé par l'appelé|
|RSP|Non volatil|Pointeur de pile|
|XMM0, YMM0|Volatil|Premier argument FP ; premier argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM1, YMM1|Volatil|Deuxième argument FP ; deuxième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM2, YMM2|Volatil|Troisième argument FP ; troisième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM3, YMM3|Volatil|Quatrième argument FP ; quatrième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM4, YMM4|Volatil|Doit être conservé si nécessaire par l'appelant ; cinquième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM5, YMM5|Volatil|Doit être conservé si nécessaire par l'appelant ; sixième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM6:XMM15, YMM6:YMM15|Non volatil (XMM), volatil (moitié supérieure de YMM)|Doit être conservé par l’appelé. Les registres YMM doivent être conservés si nécessaire par l'appelant.|

Sur la sortie de la fonction et sur l’entrée de la fonction aux appels de la bibliothèque Runtime C et les appels du système Windows, l’indicateur de direction de l’UC indicateurs register est censé être désactivée.

## <a name="see-also"></a>Voir aussi

- [Conventions des logiciels x64](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Indicateur de direction](../c-runtime-library/direction-flag.md)
