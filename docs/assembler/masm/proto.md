---
title: PROTO | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROTO
dev_langs:
- C++
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd00263f3b4a7ffcf23ccd0501989c0d40c637d
ms.sourcegitcommit: f3a5dc788e62bb36e2d9bc3e62e0aa533422408b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644061"
---
# <a name="proto"></a>PROTO

Prototypes d’une fonction ou procédure. Vous pouvez appeler la fonction prototypée par la directive PROTO à l’aide de la [INVOKE](invoke.md) directive.

## <a name="syntax"></a>Syntaxe

> *étiquette* **PROTO** \[ *distance*] \[ *langtype*] \[ __,__ \[ *paramètre*]__:__*balise*]...

### <a name="parameters"></a>Paramètres

*Étiquette*<br/>
Le nom de la fonction prototypée.

*distance*<br/>
(Facultatif) Utilisé dans les modèles de mémoire de 16 bits pour remplacer la valeur par défaut et indiquer **NEAR** ou **FAR** appels.

*langtype*<br/>
(Facultatif) Définit la convention d’appel et d’affectation de noms pour les procédures et les symboles publics. Les conventions prises en charge sont :

- 32 bits **plat** modèle : **C**, **STDCALL**

- modèles de 16 bits : **C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**

*Paramètre*<br/>
Le nom facultatif d’un paramètre de fonction.

*Balise*<br/>
Le type d’un paramètre de fonction.

Le *paramètre* et *balise* paramètres peuvent apparaître plusieurs fois, une fois pour chaque argument passé.

## <a name="example"></a>Exemple

Cet exemple montre un **PROTO** déclaration pour une fonction nommée `addup3` qui utilise un **NEAR** appel pour remplacer la valeur par défaut du modèle de 16 bits pour les appels de procédure et utilise le **C**convention d’appel de la pile pour les paramètres et valeurs de retour. Il accepte deux arguments, un **WORD** et un **VARARG**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)<br/>
[. Référence du modèle](dot-model.md)<br/>
