---
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 9df66b6c89498a2cc1a1864a668b7addfbaf593c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987871"
---
# <a name="proto"></a>PROTO

Prototype une fonction ou une procédure. Vous pouvez appeler la fonction prototypée par la directive PROTO à l’aide de la directive [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *étiquette* **proto** ⟦*distance*⟧ ⟦*Language-type*⟧ ⟦ __,__ ⟦*paramètre*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Parameters

*étiquette*\
Nom de la fonction prototypée.

*distance* (MASM 32 bits uniquement.) \
Facultatif Utilisé dans les modèles de mémoire 16 bits pour remplacer la valeur par défaut et indiquer des appels **proches** ou **éloignés** .

*Language-type* (MASM 32 bits uniquement.) \
Facultatif Définit la Convention d’appel et d’affectation des noms pour les procédures et les symboles publics. Les conventions prises en charge sont les suivantes :

- modèle **plat** 32 bits : **C**, **StdCall**

- modèles 16 bits : **C**, **Basic**, **Fortran**, **Pascal**, **syscall**, **StdCall**

\ de *paramètres*
Nom facultatif d’un paramètre de fonction.

\ de *balise*
Type d’un paramètre de fonction.

Le *paramètre* et les paramètres de *balise* peuvent apparaître plusieurs fois, une fois pour chaque argument passé.

## <a name="example"></a>Exemple

Cet exemple montre une déclaration **proto** pour une fonction nommée `addup3` qui utilise un appel **near** pour remplacer la valeur par défaut du modèle 16 bits pour les appels de procédure et utilise la Convention d’appel **C** pour les paramètres de la pile et les valeurs de retour. Il accepte deux arguments, un **mot** et un **vararg**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[. Référence du modèle](dot-model.md)
