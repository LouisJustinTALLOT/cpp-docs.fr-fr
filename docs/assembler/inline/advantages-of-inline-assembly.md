---
title: Avantages de l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: 7e634f78eca753487cf122ac95df55828bb64625
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169654"
---
# <a name="advantages-of-inline-assembly"></a>Avantages de l'assembly inline

**Section spécifique de Microsoft**

Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C qui est dans la portée. Il est par conséquent facile de l'intégrer au code C de votre programme. Le code assembleur pouvant être combiné inline avec des instructions C ou C++, il peut exécuter des tâches lourdes ou impossibles en C ou C++.

Les utilisations de l'assembly inline incluent :

- Fonctions d'écriture en langage assembleur.

- Sections vitesse-critique optimisation-projecteur du code.

- Rendre l'accès matériel direct pour les pilotes de périphérique.

- Prolog d'écriture et code d'épilogue pour les appels « naked ».

L'assembleur inline est un outil spécialisé. Si vous prévoyez de déplacer une application vers différents ordinateurs, vous souhaiterez probablement placer le code propre à l'ordinateur dans un module séparé. Comme l'assembleur inline ne prend pas en charge toutes les directives de données et de macros de l'assembleur de macros Microsoft (MASM), vous pouvez trouver plus pratique d'utiliser MASM pour ces modules.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
