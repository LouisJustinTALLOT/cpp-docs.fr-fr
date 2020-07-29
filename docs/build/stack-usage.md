---
title: Utilisation de la pile x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b1b1e0a8c30d5e24e81372912d5c488efce14841
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218934"
---
# <a name="x64-stack-usage"></a>Utilisation de la pile x64

Toute la mémoire au-delà de l’adresse actuelle de RSP est considérée comme volatile : le système d’exploitation, ou un débogueur, peut remplacer cette mémoire pendant une session de débogage utilisateur ou un gestionnaire d’interruptions. Par conséquent, RSP doit toujours être défini avant de tenter de lire ou d’écrire des valeurs dans un frame de pile.

Cette section décrit l’allocation d’espace de pile pour les variables locales et l’intrinsèque **alloca** .

## <a name="stack-allocation"></a>Allocation de piles

Le prologue d’une fonction est chargé d’allouer l’espace de pile pour les variables locales, les registres enregistrés, les paramètres de pile et les paramètres de registre.

La zone de paramètres est toujours au bas de la pile (même si `alloca` est utilisé), afin qu’elle soit toujours adjacente à l’adresse de retour pendant tout appel de fonction. Il contient au moins quatre entrées, mais toujours assez d’espace pour contenir tous les paramètres requis par toute fonction qui peut être appelée. Notez que l’espace est toujours alloué pour les paramètres de Registre, même si les paramètres eux-mêmes ne sont jamais hébergés dans la pile ; un appelé est garanti que de l’espace a été alloué pour tous ses paramètres. Les adresses d’hébergement sont requises pour les arguments Register afin qu’une zone contiguë soit disponible si la fonction appelée doit prendre l’adresse de la liste d’arguments (va_list) ou d’un argument individuel. Cette zone fournit également un emplacement pratique pour enregistrer les arguments du registre lors de l’exécution du thunk et en tant qu’option de débogage (par exemple, il rend les arguments faciles à trouver pendant le débogage s’ils sont stockés dans leurs adresses personnelles dans le code de prologue). Même si la fonction appelée a moins de 4 paramètres, ces 4 emplacements de pile sont détenus par la fonction appelée et peuvent être utilisés par la fonction appelée à d’autres fins que l’enregistrement des valeurs de registre de paramètres.  Par conséquent, l’appelant peut ne pas enregistrer les informations dans cette région de la pile à travers un appel de fonction.

Si l’espace est alloué dynamiquement ( `alloca` ) dans une fonction, un registre non volatil doit être utilisé comme pointeur de frame pour marquer la base de la partie fixe de la pile et ce registre doit être enregistré et initialisé dans le prologue. Notez que lorsque `alloca` est utilisé, les appels au même appelé à partir du même appelant peuvent avoir des adresses personnelles différentes pour leurs paramètres de registre.

La pile est toujours alignée sur 16 octets, sauf dans le prologue (par exemple, une fois l’adresse de retour envoyée) et, sauf indication contraire dans les [types de fonction](#function-types) pour une certaine classe de fonctions Frame.

L’exemple suivant illustre la disposition de la pile dans laquelle la fonction A appelle une fonction non-feuille B. le prologue de la fonction a a déjà alloué de l’espace pour tous les paramètres Register et Stack requis par B en bas de la pile. L’appel pousse l’adresse de retour et le prologue de B alloue de l’espace pour ses variables locales, les registres non volatiles et l’espace nécessaire pour appeler des fonctions. Si B utilise `alloca` , l’espace est alloué entre la zone de sauvegarde de la variable locale/non volatile et la zone de la pile des paramètres.

![Exemple de conversion AMD](../build/media/vcamd_conv_ex_5.png "Exemple de conversion AMD")

Lorsque la fonction B appelle une autre fonction, l’adresse de retour fait l’objet d’un push juste sous l’adresse d’hébergement pour RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Construction dynamique de la zone de pile de paramètres

Si un pointeur de frame est utilisé, l’option existe pour créer dynamiquement la zone de pile de paramètres. Cela n’est pas effectué actuellement dans le compilateur x64.

## <a name="function-types"></a>Types de fonction

Il existe essentiellement deux types de fonctions. Une fonction qui requiert un frame de pile est appelée *fonction de frame*. Une fonction qui ne requiert pas de frame de pile est appelée *fonction feuille*.

Une fonction frame est une fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatiles ou utilise la gestion des exceptions. Elle nécessite également une entrée de table de fonctions. Une fonction Frame requiert un prologue et un épilogue. Une fonction Frame peut allouer dynamiquement l’espace de pile et peut utiliser un pointeur de frame. Une fonction frame a les fonctionnalités complètes de cette norme d’appel à sa disposition.

Si une fonction Frame n’appelle pas une autre fonction, il n’est pas nécessaire d’aligner la pile (référencée dans la section [allocation de pile](#stack-allocation)).

Une fonction feuille n’a pas besoin d’une entrée de table de fonctions. Il ne peut pas apporter de modifications à des registres non volatils, y compris RSP, ce qui signifie qu’il ne peut pas appeler de fonctions ou allouer de l’espace de pile. Il est possible de laisser la pile non alignée pendant son exécution.

## <a name="malloc-alignment"></a>alignement malloc

[malloc](../c-runtime-library/reference/malloc.md) est assuré de retourner de la mémoire qui est correctement alignée pour stocker tout objet ayant un alignement fondamental et pouvant tenir dans la quantité de mémoire allouée. Un alignement *fondamental* est un alignement qui est inférieur ou égal au plus grand alignement pris en charge par l’implémentation sans spécification d’alignement. (Dans Visual C++, il s’agit de l’alignement requis pour un **`double`** , ou 8 octets. Dans le code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Par exemple, une allocation de quatre octets serait alignée sur une limite qui prend en charge un objet de quatre octets ou plus petit.

Visual C++ autorise les types qui ont un *alignement étendu*, également connus sous le nom de types *sur-alignés* . Par exemple, les types SSE [__m128](../cpp/m128.md) et `__m256` , et les types déclarés à l’aide de `__declspec(align( n ))` où `n` est supérieur à 8, ont un alignement étendu. L’alignement de la mémoire sur une limite adaptée à un objet qui requiert un alignement étendu n’est pas garanti par `malloc` . Pour allouer de la mémoire pour les types sur-alignés, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) et les fonctions associées.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) doit être aligné sur 16 octets et être également requis pour utiliser un pointeur de frame.

La pile allouée doit inclure un espace après celle-ci pour les paramètres des fonctions appelées par la suite, comme indiqué dans [allocation de pile](#stack-allocation).

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)<br/>
[droite](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
