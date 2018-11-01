---
title: Intégration WRL (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: a3c8b824d2cd932a7d284804f3f28781654045e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612119"
---
# <a name="wrl-integration-ccx"></a>Intégration WRL (C++/CX)

Vous pouvez mélanger code WRL avec le code de bibliothèque de modèles Windows Runtime C++ (WRL). Dans la même unité de traduction, vous pouvez utiliser des objets déclarés avec WRL handle-to-object (`^`) notation et WRL de pointeur intelligent (`ComPtr<T>`) notation. Toutefois, vous devez gérer manuellement les valeurs de retour et les codes d’erreur HRESULT de WRL et les exceptions de WRL.

## <a name="wrl-development"></a>Développement de WRL

Pour plus d’informations sur la conception et la consommation des composants WRL, consultez [bibliothèque de modèles Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Exemple

L’extrait de code suivant illustre l’utilisation de WRL et WRL pour consommer des classes Windows Runtime et examiner un fichier de métadonnées.

L’exemple est tiré d’un extrait de code dans le forum d’applications de génération Microsoft Store. L'auteur de cet extrait de code offre les exclusions et les conditions suivantes :

1. C++ ne fournit des API spécifiques à réfléchir sur des types Windows Runtime, mais les fichiers de métadonnées Windows (.winmd) pour un type sont totalement conformes aux fichiers de métadonnées CLR. Windows propose les nouvelles API de découverte des métadonnées (RoGetMetaDataFile) pour obtenir le fichier .winmd pour un type donné. Toutefois, l'utilisation de ces API est limitée aux développeurs C++ car il est impossible d'instancier une classe.

1. Une fois le code compilé, vous devez également passer Runtimeobject.lib et Rometadata.lib à l'Éditeur de liens.

1. Cet extrait de code est présenté comme tel. Alors qu'il est censé fonctionner correctement, il peut éventuellement contenir des erreurs.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}
```

## <a name="see-also"></a>Voir aussi

[Interopérabilité avec d’autres langages](interoperating-with-other-languages-c-cx.md)
