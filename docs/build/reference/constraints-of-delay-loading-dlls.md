---
title: Contraintes relatives aux DLL à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
ms.openlocfilehash: be5e5eb360f80e0b2ea9682f38f6787044cd3c63
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493069"
---
# <a name="constraints-of-delay-loading-dlls"></a>Contraintes relatives aux DLL à chargement différé

Des contraintes s'appliquent au chargement différé d'importations.

- Les importations de données ne peuvent pas être prises en charge. Une solution de contournement consiste à ce que vous traitiez vous-même explicitement l'importation de données en utilisant `LoadLibrary` (ou `GetModuleHandle` une fois que vous savez que l'assistant de chargement différé a chargé la DLL) et `GetProcAddress`.

- Le chargement différé de Kernel32.dll n'est pas pris en charge. Cette DLL est nécessaire pour que les routines de l'assistant de chargement différé effectuent le chargement différé.

- La [liaison](binding-imports.md) des points d’entrée qui sont transférés n’est pas prise en charge.

- Le chargement différé d'une DLL peut ne pas entraîner le même comportement du processus si des initialisations par processus surviennent au point d'entrée de la DLL chargée en différé. D’autres cas incluent le TLS statique (thread local Storage), déclaré à l’aide de [_ _ declspec (thread)](../../cpp/thread.md), qui n’est `LoadLibrary`pas géré lorsque la dll est chargée via. Le stockage local des threads (TLS) de type dynamique, via `TlsAlloc`, `TlsFree`, `TlsGetValue` et `TlsSetValue`, peut encore être utilisé dans les bibliothèques DLL statiques ou chargées en différé.

- Les pointeurs de fonction (globaux) statiques doivent être réinitialisés en fonctions importées après le premier appel à la fonction. Cela est dû au fait que la première utilisation du pointeur de fonction pointera vers le thunk.

- Actuellement, il n'existe aucun moyen de différer le chargement de certaines procédures spécifiques seulement à partir d'une DLL tout en utilisant le mécanisme d'importation normal.

- Les conventions d'appel personnalisées (telles que l'utilisation de codes de conditions sur les architectures x86) ne sont pas prises en charge. De plus, les registres à virgule flottante ne sont enregistrés sur aucune plateforme. Si votre routine d’assistance personnalisée ou vos routines de hook utilisent des types à virgule flottante, elles doivent enregistrer et restaurer complètement l’état de virgule flottante sur les ordinateurs dotés de conventions d’appel de registre avec des paramètres à virgule flottante. Soyez prudent avec le chargement différé de la DLL CRT si vous appelez des fonctions CRT qui acceptent des paramètres à virgule flottante sur une pile à coprocesseur arithmétique (NDP) dans la fonction d'aide.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](linker-support-for-delay-loaded-dlls.md)<br/>
[Fonction LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)<br/>
[GetModuleHandle, fonction](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlew)<br/>
[GetProcAddress, fonction](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)<br/>
[TlsAlloc, fonction](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)<br/>
[TlsFree, fonction](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsfree)<br/>
[TlsGetValue, fonction](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)<br/>
[TlsSetValue fonction)](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlssetvalue)
