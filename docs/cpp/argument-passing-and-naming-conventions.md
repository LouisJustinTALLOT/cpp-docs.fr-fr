---
title: Passage des arguments et Conventions de nommage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e050fa16c1a6f239d17cbda64ae4edcf531cb5b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087615"
---
# <a name="argument-passing-and-naming-conventions"></a>Passage des arguments et conventions de dénomination

**Section spécifique à Microsoft**

Les compilateurs Visual C++ vous permettent de spécifier des conventions pour passer des arguments et des valeurs de retour entre des fonctions et des appelants. Les conventions ne sont pas toutes disponibles sur toutes les plateformes prises en charge et certaines conventions utilisent des implémentations spécifiques à la plateforme. Dans la plupart des cas, les mots clés ou les commutateurs de compilation qui spécifient une convention non prise en charge sur une plateforme spécifique sont ignorés et la convention par défaut de la plateforme est utilisée.

Sur les plateformes x86, tous les arguments sont élargis à 32 bits lorsqu’ils sont passés. Les valeurs de retour sont également élargies à 32 bits et retournées dans le registre EAX, sauf pour les structures de 8 octets, qui sont retournées dans la paire de registres EDX:EAX. Les structures plus grandes sont retournées dans le registre EAX comme pointeurs vers des structures de retour masquées. Les paramètres font l'objet d'un push sur la pile de droite à gauche. Les structures qui ne sont pas des POD ne sont pas retournées dans les registres.

Le compilateur génère du code de prologue et d'épilogue pour enregistrer et restaurer les registres ESI, EDI, EBX et EBP, s'ils sont utilisés dans la fonction.

> [!NOTE]
>  Lorsqu'un struct, une union ou une classe est retourné(e) à partir d'une fonction par valeur, toutes les définitions du type doivent être identiques, sinon le programme peut échouer au moment de l'exécution.

Pour plus d’informations sur la façon de définir votre propre code de prologue et épilogue de fonction, consultez [des appels de fonction Naked](../cpp/naked-function-calls.md).

Pour plus d’informations sur la valeur par défaut conventions d’appel dans le code plateformes cibles x64, consultez [vue d’ensemble de x64 Conventions d’appel](../build/overview-of-x64-calling-conventions.md). Pour plus d’informations sur l’appel des problèmes de convention dans le code qui cible les plateformes ARM, consultez [problèmes courants de Visual C++ ARM Migration](../build/common-visual-cpp-arm-migration-issues.md).

Les conventions d’appel suivantes sont prises en charge par le compilateur Visual C/C++.

|Mot clé|Nettoyage de pile|Passage de paramètres|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Appelant|Effectue un push des paramètres sur la pile, dans l'ordre inverse (de droite à gauche)|
|[__clrcall](../cpp/clrcall.md)|N/A|Charger les paramètres sur la pile d'expression CLR dans l'ordre (de gauche à droite).|
|[__stdcall](../cpp/stdcall.md)|Appelé|Effectue un push des paramètres sur la pile, dans l'ordre inverse (de droite à gauche)|
|[__fastcall](../cpp/fastcall.md)|Appelé|Stocké dans les registres, puis fait l'objet d'un push sur la pile|
|[__thiscall](../cpp/thiscall.md)|Appelé|Objet d’un push sur la pile ; **cela** pointeur stocké dans ECX|
|[__vectorcall](../cpp/vectorcall.md)|Appelé|Stocké dans les registres, puis fait l'objet d'un push sur la pile dans l'ordre inverse (de droite à gauche)|

Pour plus d’informations, consultez [Conventions d’appel obsolètes](../cpp/obsolete-calling-conventions.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)