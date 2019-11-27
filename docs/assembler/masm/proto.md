---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 24ec2a9abc6c8b76fc81f6d412019296c53160f4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74394756"
---
# <a name="proto"></a>PROTO

Prototype une fonction ou une procédure. Vous pouvez appeler la fonction prototypée par la directive PROTO à l’aide de la directive [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *étiquette* **proto** ⟦*distance*⟧ ⟦*Language-type*⟧ ⟦ __,__ ⟦*paramètre*⟧ __:__ *tag* ... ⟧

### <a name="parameters"></a>Paramètres

*étiquette*\
Nom de la fonction prototypée.

*distance*\
Facultatif Utilisé dans les modèles de mémoire 16 bits pour remplacer la valeur par défaut et indiquer des appels **proches** ou **éloignés** .

*Language-type*\
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
