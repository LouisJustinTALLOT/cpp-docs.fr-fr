---
title: Utilisation et conservation des registres dans un assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 30b2f9ca8c658b65819709bb2e536b5aaecad676
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166670"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Utilisation et conservation des registres dans un assembly inline

**Section spécifique à Microsoft**

En général, vous ne devez pas supposer qu'un registre aura une valeur donnée lorsqu'un bloc `__asm` commence. La conservation des valeurs de registre n'est pas garantie d'un bloc `__asm` à un autre. Si vous terminez un bloc de code incorporé et que vous en démarrez un autre, vous ne pouvez pas être sûr que les registres dans le second bloc conservent les valeurs du premier bloc. Un bloc `__asm` hérite des valeurs de registre qui résultent du flux d'exécution normal.

Si vous utilisez la convention d'appel `__fastcall`, le compilateur passe les arguments de fonction dans les registres plutôt que sur la pile. Cela peut poser des problèmes dans les fonctions avec des blocs `__asm`, car une fonction n'a aucun moyen de déterminer quel paramètre figure dans quel registre. Si la fonction reçoit un paramètre dans EAX et qu'elle stocke immédiatement un autre élément dans EAX, le paramètre d'origine est perdu. En outre, vous devez conserver le registre ECX dans toute fonction déclarée avec `__fastcall`.

Pour éviter ces conflits de registre, n'utilisez pas la convention `__fastcall` pour les fonctions qui contiennent un bloc `__asm`. Si vous spécifiez la convention `__fastcall` globalement avec l'option du compilateur /Gr, déclarez chaque fonction contenant un bloc `__asm` avec `__cdecl` ou `__stdcall`. (L’attribut `__cdecl` indique au compilateur qu’il faut utiliser la convention d’appel C pour cette fonction.) Si vous ne compilez pas avec /Gr, évitez de déclarer une fonction avec l'attribut `__fastcall`.

Lorsque vous utilisez `__asm` pour écrire le langage assembleur dans des fonctions C/C++, vous n'avez pas besoin de conserver les registres EAX, EBX, ECX, EDX, ESI ou EDI. Par exemple, dans le POWER2. Exemple C dans [écriture de fonctions avec un Inline Assembly](../../assembler/inline/writing-functions-with-inline-assembly.md), le `power2` (fonction) ne conserve pas la valeur dans le registre EAX. Cependant, l'utilisation de ces registres affecte la qualité du code, car l'allocateur de registre ne peut pas les utiliser pour stocker des valeurs d'un bloc `__asm` à un autre. Par ailleurs, en utilisant EBX, ESI ou EDI dans du code assembleur inline, vous forcez le compilateur à enregistrer et à restaurer ces registres dans le prologue et l'épilogue de la fonction.

Vous devez conserver d'autres registres que vous utilisez (par exemple DS, SS, SP, BP et les registres indicateurs) pour la portée du bloc `__asm`. Vous devez conserver les registres ESP et EBP, à moins d'avoir une bonne raison de les modifier (pour changer de pile, par exemple). Consultez également [optimisation de l’Inline Assembly](../../assembler/inline/optimizing-inline-assembly.md).

Certains types SSE requièrent l'alignement de pile sur huit octets, ce qui force le compilateur à émettre du code d'alignement de pile dynamique. Pour pouvoir accéder aux variables locales et aux paramètres de fonction après l'alignement, le compilateur tient à jour deux pointeurs de frame.  Si le compilateur effectue l’omission du pointeur frame (FPO), il utilise EBP et ESP.  Si le compilateur n’effectue pas FPO, il utilise EBX et EBP. Pour garantir l'exécution correcte du code, ne modifiez pas EBX dans le code asm si la fonctionnalité requiert l'alignement de pile dynamique, car cela peut modifier le pointeur de frame. Déplacez les types alignés sur huit octets hors de la fonction ou évitez d'utiliser EBX.

> [!NOTE]
>  Si votre code assembleur inline modifie l'indicateur de direction à l'aide des instructions STD ou CLD, vous devez restaurer l'indicateur à sa valeur d'origine.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>