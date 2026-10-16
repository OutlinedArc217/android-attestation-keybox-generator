# Android Attestation Keybox 生成工具

**这个PoC已经被咕噜咕噜(Google)制裁了**

此工具用于生成符合 **Android Attestation** 格式的 **Keybox** 文件，包含设备私钥、证书以及相关配置信息。你可以使用此工具为 Android 设备生成 Keybox 文件，并在设备验证过程中使用该文件。


```bash
cat keybox.xml
```

该文件包含了设备 ID、私钥和证书等信息，格式符合 **Android Attestation** 的要求。

## 脚本解析

1. **生成设备 ID：** 使用 `openssl rand` 随机生成一个设备 ID。
2. **生成 CA 私钥和证书：** 使用 **ECDSA** 算法生成 CA 密钥，并签署一个自签名证书。
3. **生成设备私钥和证书：** 同样使用 **ECDSA** 算法生成设备私钥，并由 CA 签署生成设备证书。
4. **输出 Keybox 文件：** 将生成的私钥和证书嵌入到符合 **AndroidAttestation** 格式的 XML 文件中。

## 文件结构

执行脚本后，你将得到以下文件：

- **ca.key**：根证书私钥（用于签署设备证书）
- **ca.crt**：根证书（自签名）
- **device.key**：设备私钥
- **device.csr**：设备证书签名请求
- **device.crt**：设备证书
- **keybox.xml**：符合 Android Attestation 格式的 Keybox 文件

## 注意事项

- 生成的 Keybox 文件可以过Google的DEVICE

## License

本项目使用 **MIT License**，详情请参阅 [LICENSE](LICENSE) 文件。
