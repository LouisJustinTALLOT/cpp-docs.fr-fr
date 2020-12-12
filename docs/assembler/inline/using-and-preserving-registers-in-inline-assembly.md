---
description: 'En savoir plus sur les éléments suivants : utilisation et préservation des registres dans un assembly inline'
title: Utilisation et conservation des registres dans un assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], register values
- inline assembly, registers
- registers, inline assembly
- preserving registers
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
ms.openlocfilehash: 36758a313044190c9ee2f2a9b094325821d87635
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122003"
---
# <a name="using-and-preserving-registers-in-inline-assembly"></a>Utilisation et conservation des registres dans un assembly inline

**Spécifique à Microsoft**

En général, vous ne devez pas supposer qu’un registre aura une valeur donnée au début d’un **`__asm`** bloc. Il n’est pas garanti que les valeurs de registre soient conservées dans des **`__asm`** blocs séparés. Si vous terminez un bloc de code incorporé et que vous en démarrez un autre, vous ne pouvez pas être sûr que les registres dans le second bloc conservent les valeurs du premier bloc. Un **`__asm`** bloc hérite des valeurs de Registre qui résultent du déroulement normal du contrôle.

Si vous utilisez la **`__fastcall`** Convention d’appel, le compilateur passe les arguments de fonction dans les registres plutôt que sur la pile. Cela peut créer des problèmes dans les fonctions avec des **`__asm`** blocs, car une fonction n’a aucun moyen de déterminer le paramètre dans lequel inscrire. Si la fonction reçoit un paramètre dans EAX et qu'elle stocke immédiatement un autre élément dans EAX, le paramètre d'origine est perdu. En outre, vous devez conserver le registre ECX dans toutes les fonctions déclarées avec **`__fastcall`** .

Pour éviter de tels conflits de registres, n’utilisez pas la **`__fastcall`** Convention pour les fonctions qui contiennent un **`__asm`** bloc. Si vous spécifiez la **`__fastcall`** Convention globalement avec l’option du compilateur/gr, déclarez chaque fonction contenant un **`__asm`** bloc avec **`__cdecl`** ou **`__stdcall`** . (L' **`__cdecl`** attribut indique au compilateur d’utiliser la Convention d’appel C pour cette fonction.) Si vous ne compilez pas avec/gr, évitez de déclarer la fonction avec l' **`__fastcall`** attribut.

Lorsque **`__asm`** vous utilisez pour écrire le langage assembleur dans des fonctions C/C++, vous n’avez pas besoin de conserver les registres EAX, EBX, ecx, EDX, ESI ou EDI. Par exemple, dans le POWER2. Exemple C dans l' [écriture de fonctions avec un assembly inline](../../assembler/inline/writing-functions-with-inline-assembly.md), la `power2` fonction ne conserve pas la valeur dans le registre EAX. Toutefois, l’utilisation de ces registres affecte la qualité du code, car l’allocateur de registre ne peut pas les utiliser pour stocker des valeurs entre les **`__asm`** blocs. Par ailleurs, en utilisant EBX, ESI ou EDI dans du code assembleur inline, vous forcez le compilateur à enregistrer et à restaurer ces registres dans le prologue et l'épilogue de la fonction.

Vous devez conserver les autres registres que vous utilisez (tels que les registres DS, SS, SP, BP et indicateurs) pour l’étendue du **`__asm`** bloc. Vous devez conserver les registres ESP et EBP, à moins d'avoir une bonne raison de les modifier (pour changer de pile, par exemple). Voir aussi [optimisation de l’assembly inline](../../assembler/inline/optimizing-inline-assembly.md).

Certains types SSE requièrent l'alignement de pile sur huit octets, ce qui force le compilateur à émettre du code d'alignement de pile dynamique. Pour pouvoir accéder aux variables locales et aux paramètres de fonction après l'alignement, le compilateur tient à jour deux pointeurs de frame.  Si le compilateur effectue une omission du pointeur de frame (FPO), il utilise EBP et ESP.  Si le compilateur n’exécute pas FPO, il utilise EBX et EBP. Pour garantir l'exécution correcte du code, ne modifiez pas EBX dans le code asm si la fonctionnalité requiert l'alignement de pile dynamique, car cela peut modifier le pointeur de frame. Déplacez les types alignés sur huit octets hors de la fonction ou évitez d'utiliser EBX.

> [!NOTE]
> Si votre code assembleur inline modifie l'indicateur de direction à l'aide des instructions STD ou CLD, vous devez restaurer l'indicateur à sa valeur d'origine.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
