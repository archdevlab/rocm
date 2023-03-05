# _     _            _        _          _____
#| |__ | | __ _  ___| | _____| | ___   _|___ /
#| '_ \| |/ _` |/ __| |/ / __| |/ / | | | |_ \
#| |_) | | (_| | (__|   <\__ \   <| |_| |___) |
#|_.__/|_|\__,_|\___|_|\_\___/_|\_\\__, |____/
#                                  |___/

#Maintainer: blacksky3 <https://github.com/blacksky3>
#Credits: Carson Rueter <roachh at proton mail dot com>
#Credits: George Sofianos

major=5.4.3
major_short=5.4.3
minor=50403-121
ubuntu_ver=22.04
repo_folder_ver=5.4.3

llvm_ver=15.0.0.23045
cmake_ver=0.8.0
devicelibs_ver=1.0.0
comgr_ver=2.4.0
hsakmt_ver=20221020.0.2
hsa_ver=1.7.0
rocminfo_ver=1.0.0
rocmopencl_ver=2.0.0
rocmoclicd_ver=2.0.0
rocmclang_ver=0.5.0

pkgname=rocm-stack
pkgver=${major}
pkgrel=1
pkgdesc='AMD Complete ROCM stack (OpenCL implementation for AMD) (officially supporting GFX8 and later cards (Fiji, Polaris, Vega), with unofficial and partial support for Navi10 based cards)'
arch=(x86_64)
url='https://repo.radeon.com/rocm'
license=(MIT)
depends=('cmake' 'numactl' 'pciutils' 'libdrm' 'libelf' 'python' 'mesa' 'opencl-icd-loader')
conflicts=(rocm-llvm rocm-cmake rocm-device-libs comgr hsakmt-roct hsa-rocr rocminfo rocm-opencl-runtime rocm-clang-ocl)
provides=(rocm-llvm rocm-cmake rocm-device-libs comgr hsakmt-roct hsa-rocr rocminfo rocm-opencl-runtime rocm-clang-ocl)
source=(https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-llvm/rocm-llvm_${llvm_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-cmake/rocm-cmake_${cmake_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-device-libs/rocm-device-libs_${devicelibs_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/c/comgr/comgr_${comgr_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsakmt-roct-dev/hsakmt-roct-dev_${hsakmt_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr/hsa-rocr_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr-dev/hsa-rocr-dev_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocminfo/rocminfo_${rocminfo_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl/rocm-opencl_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-dev/rocm-opencl-dev_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-runtime/rocm-opencl-runtime_${major_short}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-ocl-icd/rocm-ocl-icd_${rocmoclicd_ver}.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-clang-ocl/rocm-clang-ocl_${rocmclang_ver}.${minor}~${ubuntu_ver}_amd64.deb)

extract_debgz(){
  local tmpdir="$(basename "${1%.deb}")"
  rm -Rf "$tmpdir"
  mkdir "$tmpdir"
  cd "$tmpdir"
  ar x "$1"
  tar -C "${pkgdir}" -xf data.tar.gz
}

extract_debxz(){
  local tmpdir="$(basename "${1%.deb}")"
  rm -Rf "$tmpdir"
  mkdir "$tmpdir"
  cd "$tmpdir"
  ar x "$1"
  tar -C "${pkgdir}" -xf data.tar.xz
}

package_rocm-stack(){
  extract_debgz "${srcdir}"/rocm-llvm_${llvm_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-cmake_${cmake_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-device-libs_${devicelibs_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/comgr_${comgr_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsakmt-roct-dev_${hsakmt_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr-dev_${hsa_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocminfo_${rocminfo_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-dev_${rocmopencl_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-runtime_${major_short}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-ocl-icd_${rocmoclicd_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-clang-ocl_${rocmclang_ver}.${minor}~${ubuntu_ver}_amd64.deb

  mv "${pkgdir}/opt/rocm-5.4.3/" "${pkgdir}/opt/rocm/"

  install -dm755 "${pkgdir}"/usr/share/licenses/rocm
  install -dm755 "${pkgdir}"/usr/share/doc/rocm

  # hsakmt-roct
  sed -i "s#prefix=/opt/rocm-5.4.3#prefix=/opt/rocm#g" "${pkgdir}"/opt/rocm/share/pkgconfig/libhsakmt.pc
  echo '/opt/rocm/lib' > "hsakmt-roct.conf"
  install -Dm644 "hsakmt-roct.conf" "$pkgdir/etc/ld.so.conf.d/hsakmt-roct.conf"

  # hsa-rocr
  echo "/opt/rocm/hsa/lib" > "hsa-rocr.conf"
  install -Dm644 "hsa-rocr.conf" "$pkgdir/etc/ld.so.conf.d/hsa-rocr.conf"

  # comgr
  # Place README.md in doc dir
  install -dm755 "${pkgdir}"/usr/share/doc/rocm/amd_comgr
  mv "${pkgdir}/opt/rocm/share/doc/amd_comgr/README.md" "${pkgdir}/usr/share/doc/rocm/amd_comgr/"

  # rocm-opencl-runtime
  echo '/opt/rocm/lib' > "rocm-opencl-runtime.conf"
  install -Dm644 "rocm-opencl-runtime.conf" "$pkgdir/etc/ld.so.conf.d/rocm-opencl-runtime.conf"
  echo '/opt/rocm/lib/libamdocl64.so' > 'amdocl64.icd'
  install -Dm644 'amdocl64.icd' "$pkgdir/etc/OpenCL/vendors/amdocl64.icd"

  # Install license
  # rocm-llvm
  mv "${pkgdir}/opt/rocm/share/doc/rocm-llvm" "${pkgdir}/usr/share/licenses/rocm/"
  # rocm-llvm
  mv "${pkgdir}/opt/rocm/share/doc/rocm-cmake" "${pkgdir}/usr/share/licenses/rocm/"
  # ROCm-Device-Libs
  mv "${pkgdir}/opt/rocm/share/doc/ROCm-Device-Libs" "${pkgdir}/usr/share/licenses/rocm/"
  # comgr
  mv "${pkgdir}/opt/rocm/share/doc/amd_comgr" "${pkgdir}/usr/share/licenses/rocm/"
  # hsakmt-roct-dev
  mv "${pkgdir}/opt/rocm/share/doc/hsakmt" "${pkgdir}/usr/share/licenses/rocm/"
  # hsa-rocr
  mv "${pkgdir}/opt/rocm/share/doc/hsa-runtime64" "${pkgdir}/usr/share/licenses/rocm/"
  # rocminfo
  mv "${pkgdir}/opt/rocm/share/doc/rocminfo" "${pkgdir}/usr/share/licenses/rocm/"
  # opencl/ocl-icd
  mv "${pkgdir}/opt/rocm/share/doc/opencl" "${pkgdir}/usr/share/licenses/rocm/"
  mv "${pkgdir}/opt/rocm/share/doc/rocm-ocl-icd" "${pkgdir}/usr/share/licenses/rocm/"
  # rocm-clang-ocl
  mv "${pkgdir}/opt/rocm/share/doc/rocm-clang-ocl" "${pkgdir}/usr/share/licenses/rocm/"

  # Remove empty doc dir
  rm -rf "${pkgdir}/opt/rocm/share/doc"
}

sha256sums=('56c2cc6600afd3d8128252c9d8be4f8454e7109772d15bd809bb643eb2895ee6'
            'b6a76abe01ea7c12faf0d57344195e0fd0638da19dcc6ccc5829d6dc32dcb227'
            '4007016d604907c83ae999b82f012913f068b35e89cbdb81ae55461d0c6a11bd'
            'b966685a075d15b50d9d68f053e72b23cfcb627802fb507fdd24357a84fa48dc'
            '20278f31d37f9e155f77305004d6bdc6f4f5c3a8dc67073bad3d54e5addb11fc'
            'c3e340563e7f2a8789652f2e7ddb52d47a5bf267f85d930208be3d71da970102'
            '902ebb03ea6dd500170d7c4709b70d3b313218c260934085d19d73dd5dec5d09'
            'df6723c34165f0f067e725654d37fcb9b4365230d5342fef10271c19edf2b6aa'
            'c77907c7ac874a86e20b32d5d86c649ce84abfec88679263892c5ff508722580'
            '1e88bb3d0be13283f81e9baa111343e68909f908a4184c319a12a2614c4927d2'
            '5d48de32129a390218f07ebfd6b2c67d72d5a1bdaa220e9c2cbab31a6464f80c'
            '1457c69a3b11eba803f340fcc958394c03860cbed788cc936d7e017f61e11c8a'
            'b17da12f31c85890768c31da5f40ac93663a1b6f489c45dd32422d1345d8e3c4')
