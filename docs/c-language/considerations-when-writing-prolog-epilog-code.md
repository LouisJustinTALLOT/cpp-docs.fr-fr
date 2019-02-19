---
title: Considérations relatives à l'écriture du code de prologue-épilogue
ms.date: 11/04/2016
helpviewer_keywords:
- layouts, stack frame
- stack frame layout
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: 3b8addec-e809-48e4-b1d0-5bad133bd4b8
ms.openlocfilehash: 52403fc45bbb68d693ef154bf39c5dd366dd10c5
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146480"
---
# <a name="considerations-when-writing-prologepilog-code"></a>Considérations relatives à l'écriture du code de prologue/épilogue

**Section spécifique à Microsoft**

Avant d'écrire vos propres séquences de code de prologue et d'épilogue, il importe de comprendre comment le frame de pile est disposé. Il est également utile de savoir utiliser la constante prédéfinie **__LOCAL_SIZE**.

##  <a name="_clang_c_stack_frame_layout"></a> Disposition du frame de pile C

Cet exemple montre le code de prologue standard qui peut apparaître dans une fonction 32 bits :

```
push     ebp                 ; Save ebp
mov      ebp, esp            ; Set stack frame pointer
sub      esp, localbytes     ; Allocate space for locals
push     <registers>         ; Save registers
```

La variable `localbytes` représente le nombre d'octets nécessaires sur la pile pour les variables locales. La variable `registers` est un espace réservé qui représente la liste de registres à enregistrer sur la pile. Après avoir effectué un push des registres, vous pouvez placer toutes les autres données pertinentes sur la pile. Voici le code d'épilogue correspondant :

```
pop      <registers>         ; Restore registers
mov      esp, ebp            ; Restore stack pointer
pop      ebp                 ; Restore ebp
ret                          ; Return from function
```

La pile se réduit toujours (des adresses de mémoire supérieures aux adresses de mémoire inférieures). Le pointeur de base (`ebp`) pointe vers la valeur de `ebp` qui fait l'objet d'un push. La zone de variables locales commence à `ebp-2`. Pour accéder aux variables locales, calculez un décalage à partir de `ebp` en soustrayant la valeur appropriée de `ebp`.

##  <a name="_clang_the___local_size_constant"></a>La constante __LOCAL_SIZE

Le compilateur fournit une constante, **__LOCAL_SIZE**, à utiliser dans le bloc assembleur inline de code de prologue de fonction. Cette constante est utilisée pour allouer de l'espace pour les variables locales sur le frame de pile dans le code de prologue personnalisé.

Le compilateur détermine la valeur de **__LOCAL_SIZE**. Cette valeur est le nombre total d'octets de toutes les variables locales définies par l'utilisateur et des variables temporaires générées par le compilateur. La constante **__LOCAL_SIZE** peut être utilisée uniquement comme opérande immédiat. Elle ne peut pas être utilisée dans une expression. Vous ne devez pas modifier ou redéfinir la valeur de cette constante. Par exemple :

```
mov      eax, __LOCAL_SIZE           ;Immediate operand--Okay
mov      eax, [ebp - __LOCAL_SIZE]   ;Error
```

L'exemple suivant d'une fonction naked contenant des séquences de prologue et d'épilogue personnalisées utilise **__LOCAL_SIZE** dans la séquence de prologue :

```
__declspec ( naked ) func()
{
   int i;
   int j;

   __asm      /* prolog */
      {
      push   ebp
      mov      ebp, esp
      sub      esp, __LOCAL_SIZE
      }

   /* Function body */

   __asm      /* epilog */
      {
      mov      esp, ebp
      pop      ebp
      ret
      }
}
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonctions naked](../c-language/naked-functions.md)
