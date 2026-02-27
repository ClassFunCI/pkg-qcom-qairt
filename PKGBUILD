# Maintainer: Xilin Wu <sophon@radxa.com>

pkgbase=qcom-qairt
pkgname=('qcom-qnn-sdk-v68' 'qcom-snpe-sdk-v68')
pkgver=2.43.1.260218
pkgrel=1
arch=('aarch64')
url="https://softwarecenter.qualcomm.com"
license=('custom:Qualcomm-Technologies-Inc.-Proprietary')
makedepends=('unzip')
options=('!strip' '!debug')

_hexagon_version="v68"
_hexagon_dir="hexagon-${_hexagon_version}"
_qnpsdk_src_ver=${pkgver}
_qnpsdk_src_shid="4b36d5fce64f32c6be2bfaeff506e22bd737ff85190605ee1d3bf2dc6495fc81"
_platform_dir="aarch64-oe-linux-gcc11.2"

source=("https://softwarecenter.qualcomm.com/api/download/software/sdks/Qualcomm_AI_Runtime_Community/All/${_qnpsdk_src_ver}/v${_qnpsdk_src_ver}.zip")
sha256sums=("${_qnpsdk_src_shid}")

package_qcom-qnn-sdk-v68() {
    pkgdesc="Qualcomm Neural Network SDK (Hexagon v68)"
    provides=('qcom-qnn-sdk')
    depends=()

    local _qnn_dir="${srcdir}/qairt/${_qnpsdk_src_ver}"

    install -d "${pkgdir}/usr/bin"
    install -d "${pkgdir}/usr/include"
    install -d "${pkgdir}/usr/lib/rfsa/adsp"
    install -d "${pkgdir}/usr/share/licenses/${pkgname}"

    # Libraries
    install -m 0755 ${_qnn_dir}/lib/${_platform_dir}/*Qnn* "${pkgdir}/usr/lib/"
    install -m 0755 "${_qnn_dir}/lib/${_platform_dir}/libPlatformValidatorShared.so" "${pkgdir}/usr/lib/"
    install -m 0755 "${_qnn_dir}/lib/${_platform_dir}/libcalculator.so" "${pkgdir}/usr/lib/"

    # Binaries
    install -m 0755 ${_qnn_dir}/bin/${_platform_dir}/qnn* "${pkgdir}/usr/bin/"
    install -m 0755 "${_qnn_dir}/bin/${_platform_dir}/qtld-net-run" "${pkgdir}/usr/bin/"

    # Hexagon DSP libraries
    install -m 0755 ${_qnn_dir}/lib/${_hexagon_dir}/unsigned/libQnn* "${pkgdir}/usr/lib/rfsa/adsp/"
    install -m 0755 "${_qnn_dir}/lib/${_hexagon_dir}/unsigned/libCalculator_skel.so" "${pkgdir}/usr/lib/rfsa/adsp/"

    # Headers
    cp -r "${_qnn_dir}/include/QNN/"* "${pkgdir}/usr/include/"
    chmod -R 0755 "${pkgdir}/usr/include/"

    # License
    install -m 0644 "${_qnn_dir}/LICENSE.pdf" "${pkgdir}/usr/share/licenses/${pkgname}/"
}

package_qcom-snpe-sdk-v68() {
    pkgdesc="Snapdragon Neural Processing Engine SDK (Hexagon v68)"
    provides=('qcom-snpe-sdk')
    depends=()

    local _snpe_dir="${srcdir}/qairt/${_qnpsdk_src_ver}"

    install -d "${pkgdir}/usr/bin"
    install -d "${pkgdir}/usr/include"
    install -d "${pkgdir}/usr/lib/rfsa/adsp"
    install -d "${pkgdir}/usr/share/licenses/${pkgname}"

    # Libraries
    install -m 0755 ${_snpe_dir}/lib/${_platform_dir}/*Snpe* "${pkgdir}/usr/lib/"
    install -m 0755 "${_snpe_dir}/lib/${_platform_dir}/libSNPE.so" "${pkgdir}/usr/lib/"
    install -m 0755 "${_snpe_dir}/lib/${_platform_dir}/libhta_hexagon_runtime_snpe.so" "${pkgdir}/usr/lib/"

    # Binaries
    install -m 0755 ${_snpe_dir}/bin/${_platform_dir}/snpe* "${pkgdir}/usr/bin/"

    # Hexagon DSP libraries
    install -m 0755 ${_snpe_dir}/lib/${_hexagon_dir}/unsigned/libSnpe* "${pkgdir}/usr/lib/rfsa/adsp/"

    # Headers
    cp -r "${_snpe_dir}/include/SNPE/"* "${pkgdir}/usr/include/"
    chmod -R 0755 "${pkgdir}/usr/include/"

    # License
    install -m 0644 "${_snpe_dir}/LICENSE.pdf" "${pkgdir}/usr/share/licenses/${pkgname}/"
}