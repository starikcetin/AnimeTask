# Depreciation Notice:

This fork is no longer maintained since the [main repository](https://github.com/kyubuns/AnimeTask) has adopted UPM support. Published versions should still work, but you should consider updating your package version to one of the versions published by the main repository.

---

[![openupm](https://img.shields.io/npm/v/com.kyubuns.animetask?label=openupm&registry_uri=https://package.openupm.com)](https://openupm.com/packages/com.kyubuns.animetask/)

This repository has UPM support. You can install it as follows:

```
npm install -g openupm-cli
openupm add com.kyubuns.animetask
```

[Google Translate from Japanese](https://translate.googleusercontent.com/translate_c?client=tw-ob&depth=1&hl=en&ie=UTF8&rurl=translate.google.com&sl=ja&sp=nmt4&tl=en&u=https://github.com/starikcetin/AnimeTask&usg=ALkJrhijxNZb85Ffks0H2Ng16hLv-4HFCA)

---

# AnimeTask

Task Animation Library for Unity

![image](https://user-images.githubusercontent.com/961165/46568998-56470e80-c989-11e8-8798-c168a1c6b494.gif)

## Instructions

- Import [UnityPackage](https://github.com/kyubuns/AnimeTask/releases)

## Sample

### Basic

`(-5f, 0f, 0f)` から `(5f, 0f, 0f)` へ2秒かけて移動する。

```csharp
await Anime.Play(
    Easing.Create<Linear>(new Vector3(-5f, 0f, 0f), new Vector3(5f, 0f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### PlayTo

PlayToを利用すると、現在地から移動する。

```csharp
await Anime.PlayTo(
    Easing.Create<Linear>(new Vector3(-5f, 3f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### Easing

EasingのInCubicを利用して移動する。

```csharp
await Anime.PlayTo(
    Easing.Create<InCubic>(new Vector3(-5f, 3f, 0f), 2f),
    TranslateTo.LocalPosition(cube)
);
```

### TranslateTo.Action

TranslateTo.Actionを利用すると、アニメーションした値を自由に使用出来る。

```csharp
await Anime.Play(
    Easing.Create<Linear>(0, 100, 2f),
    TranslateTo.Action<float>(x => Debug.Log(x))
);
```

## UniTask(UniRx.Async)を利用する

[UniTask](https://github.com/neuecc/UniRx)を利用することでパフォーマンスの向上が見込めます。

- UniTaskを利用できる状態にする。
- AnimeTaskのAssembly DefinitionにUniRx.Asyncの参照を追加する。
<img width="400" alt="unitask1" src="https://user-images.githubusercontent.com/961165/46583321-2afb1700-ca90-11e8-8591-e5d32b76a57d.png">
- BuildSettingsのScripting Define Symbolsに `ENABLE_UNITASK` を追加する。
<img width="300" alt="unitask2" src="https://user-images.githubusercontent.com/961165/46583322-2afb1700-ca90-11e8-9208-e73856fe3684.png">

## Requirements

- Requires Unity2017.1 or later with .net4.6

## License

MIT License (see [LICENSE](LICENSE))

