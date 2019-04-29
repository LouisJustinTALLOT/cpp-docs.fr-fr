---
title: l’utilisation de la pile x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 902e4304ac124be46c6edf0860118dc522b34890
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314812"
---
# <a name="x64-stack-usage"></a>l’utilisation de la pile x64

Toute la mémoire au-delà de l’adresse actuelle de RSP est considérée comme volatile : Le système d’exploitation ou d’un débogueur, peut remplacer cette mémoire pendant une session de débogage d’utilisateur ou un gestionnaire d’interruption. Par conséquent, RSP doit toujours être défini avant de tenter de lire ou écrire des valeurs dans un frame de pile.

Cette section décrit l’allocation d’espace de pile pour les variables locales et le **alloca** intrinsèque.

## <a name="stack-allocation"></a>Allocation de piles

Prologue d’une fonction est responsable de l’allocation d’espace de pile pour les variables locales, les registres enregistrés, paramètres de la pile et les paramètres de Registre.

La zone paramètre est toujours en bas de la pile (même si `alloca` est utilisé), afin qu’il s’agit toujours adjacente à l’adresse de retour pendant un appel de fonction. Il contient au moins quatre entrées, mais toujours suffisamment d’espace pour contenir tous les paramètres requis par n’importe quelle fonction qui peut être appelée. Notez que l’espace est toujours alloué pour les paramètres de Registre, même si les paramètres proprement dits ne sont jamais hébergés dans la pile ; un appelant est garanti qu’espace a été alloué pour tous ses paramètres. Adresses personnelles sont requis pour les arguments de Registre pour une zone contiguë soit disponible au cas où la fonction appelée doit prendre l’adresse de la liste d’arguments (va_list) ou un argument particulier. Cette zone fournit également un emplacement pratique pour enregistrer des arguments de Registre pendant l’exécution de la conversion de code et en tant qu’option de débogage (par exemple, rend les arguments faciles à trouver pendant le débogage s’ils sont stockés à leur adresse d’origine dans le code de prologue). Même si la fonction appelée possède moins de 4 paramètres, ces 4 emplacements de pile sont en réalité détenus par la fonction appelée et peuvent être utilisées par la fonction appelée à d’autres fins que l’enregistrement des valeurs de registres de paramètre.  Par conséquent, l’appelant peut enregistrer les informations dans cette région de pile après un appel de fonction.

Si l’espace est alloué dynamiquement (`alloca`) dans une fonction, puis un Registre non volatil doit être utilisé comme pointeur de frame pour marquer la base de la partie fixe de la pile et que le Registre doit être enregistré et initialisé dans le prologue. Notez que lorsque `alloca` est utilisé, les appels au même appelé à partir de l’appelant même peuvent avoir des adresses d’origine différentes pour leurs paramètres de Registre.

La pile sera toujours maintenue 16 octets alignés, sauf dans le prologue (par exemple, une fois que l’adresse de retour est l’objet d’un push) et à l’endroit indiqué dans [Types de fonction](#function-types) pour une certaine classe de fonctions de trame.

Voici un exemple de la disposition de pile où la fonction A appelle un non-feuille fonction prologue de B. la fonction A a déjà alloué espace pour tous les paramètres de Registre et de pile requis par B en bas de la pile. L’appel exécute un push de l’adresse de retour et le prologue de B alloue de l’espace pour ses variables locales, les registres non volatils et l’espace nécessaire pour qu’il puisse appeler les fonctions. Si B utilise `alloca`, l’espace est alloué entre le Registre local de la variable/non volatile zone de sauvegarde et de la zone paramètre de la pile.

![Exemple de conversion AMD](../build/media/vcamd_conv_ex_5.png "AMDConversionExample")

Lorsque la fonction B appelle une autre fonction, l’adresse de retour est envoyée juste en dessous de l’adresse personnelle pour RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Construction de zone de pile de paramètre dynamique

Si un pointeur de frame est utilisé, l’option existe pour créer dynamiquement la zone paramètre de la pile. Cela n’est pas actuellement effectuée dans le x64 compilateur.

## <a name="function-types"></a>Types de fonction

Il existe essentiellement deux types de fonctions. Une fonction qui nécessite un frame de pile est appelée un *frame fonction*. Une fonction qui ne nécessite pas d’un frame de pile est appelée un *feuille fonction*.

Une fonction de frame est une fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions. Elle requiert également une entrée de table de fonction. Une fonction de frame exige un prologue et un épilogue. Une fonction de frame peut allouer dynamiquement de l’espace de pile et pouvez employer un pointeur de frame. Une fonction de frame a toutes les fonctionnalités de cet appel standard à sa disposition.

Si une fonction de frame n’appelle pas une autre fonction, il n’est pas nécessaire d’aligner la pile (référencé dans la Section [Allocation de piles](#stack-allocation)).

Une feuille est une fonction qui ne nécessite pas une entrée de table de fonction. Il ne peut pas apporter des modifications pour les registres non volatils, y compris RSP, ce qui signifie qu’il ne peut pas appeler des fonctions ou allouer de l’espace de pile. Il est autorisé à laisser la pile non alignés lors de son exécution.

## <a name="malloc-alignment"></a>alignement de malloc

[malloc](../c-runtime-library/reference/malloc.md) est garanti pour retourner une mémoire qui est correctement alignée pour stocker un objet qui a un alignement simple et qui peut contenir la quantité de mémoire qui est allouée. Un *alignement fondamental* est un alignement qui est inférieure ou égale à la plus grand alignement pris en charge par l’implémentation sans spécification d’alignement. (Dans Visual C++, il s’agit d’alignement qui est requis pour un `double`, ou 8 octets. Dans un code qui cible les plateformes 64 bits, il s’agit de 16 octets.) Par exemple, une allocation de quatre octets serait alignée sur une limite qui prend en charge de n’importe quel objet de quatre octets ou plus petits.

Visual C++ permet les types qui ont *alignement étendu*, également appelés *sur-alignés* types. Par exemple, les types de SSE [__m128](../cpp/m128.md) et `__m256`et les types qui sont déclarés à l’aide de `__declspec(align( n ))` où `n` est supérieure à 8, ont un alignement étendu. Alignement de la mémoire sur une limite qui est adaptée à un objet qui requiert l’alignement étendu n’est pas garanti par `malloc`. Pour allouer de mémoire pour les types sur-alignés, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) et des fonctions associées.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) doit être de 16 octets alignée et utiliser un pointeur de frame.

La pile est allouée doit inclure l’espace après lui pour les paramètres des fonctions appelées par la suite, comme indiqué dans [Allocation de piles](#stack-allocation).

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
