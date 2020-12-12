---
description: En savoir plus sur la réussite des arguments et les conventions d’affectation des noms
title: Passage des arguments et conventions de dénomination
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: bd51187fcc65dfce6c473c784c85c6afcae0bcf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239829"
---
# <a name="argument-passing-and-naming-conventions"></a>Passage des arguments et conventions de dénomination

**Spécifique à Microsoft**

Les compilateurs Microsoft C++ vous permettent de spécifier des conventions pour passer des arguments et des valeurs de retour entre les fonctions et les appelants. Les conventions ne sont pas toutes disponibles sur toutes les plateformes prises en charge et certaines conventions utilisent des implémentations spécifiques à la plateforme. Dans la plupart des cas, les mots clés ou les commutateurs de compilation qui spécifient une convention non prise en charge sur une plateforme spécifique sont ignorés et la convention par défaut de la plateforme est utilisée.

Sur les plateformes x86, tous les arguments sont étendus à 32 bits lorsqu’ils sont passés. Les valeurs de retour sont également élargies à 32 bits et retournées dans le registre EAX, sauf pour les structures de 8 octets, qui sont retournées dans la paire de registres EDX:EAX. Les structures plus grandes sont retournées dans le registre EAX comme pointeurs vers des structures de retour masquées. Les paramètres font l'objet d'un push sur la pile de droite à gauche. Les structures qui ne sont pas des POD ne sont pas retournées dans les registres.

Le compilateur génère du code de prologue et d'épilogue pour enregistrer et restaurer les registres ESI, EDI, EBX et EBP, s'ils sont utilisés dans la fonction.

> [!NOTE]
> Lorsqu'un struct, une union ou une classe est retourné(e) à partir d'une fonction par valeur, toutes les définitions du type doivent être identiques, sinon le programme peut échouer au moment de l'exécution.

Pour plus d’informations sur la façon de définir votre propre prologue de fonction et le code d’épilogue, consultez [appels de fonction Naked](../cpp/naked-function-calls.md).

Pour plus d’informations sur les conventions d’appel par défaut dans le code qui cible les plateformes x64, consultez [Convention d’appel x64](../build/x64-calling-convention.md). Pour plus d’informations sur les problèmes de convention d’appel dans le code qui cible les plateformes ARM, consultez [problèmes courants de Migration Visual C++ Arm](../build/common-visual-cpp-arm-migration-issues.md).

Les conventions d'appel suivantes sont prises en charge par le compilateur Visual C/C++.

|Mot clé|Nettoyage de pile|Passage de paramètres|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Appelant|Effectue un push des paramètres sur la pile, dans l'ordre inverse (de droite à gauche)|
|[__clrcall](../cpp/clrcall.md)|n/a|Charger les paramètres sur la pile d'expression CLR dans l'ordre (de gauche à droite).|
|[__stdcall](../cpp/stdcall.md)|Appelé|Effectue un push des paramètres sur la pile, dans l'ordre inverse (de droite à gauche)|
|[__fastcall](../cpp/fastcall.md)|Appelé|Stocké dans les registres, puis fait l'objet d'un push sur la pile|
|[__thiscall](../cpp/thiscall.md)|Appelé|Push effectué sur la pile ; **`this`** pointeur stocké dans ecx|
|[__vectorcall](../cpp/vectorcall.md)|Appelé|Stocké dans les registres, puis fait l'objet d'un push sur la pile dans l'ordre inverse (de droite à gauche)|

Pour obtenir des informations connexes, consultez [conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
