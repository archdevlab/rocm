# _     _            _        _          _____
#| |__ | | __ _  ___| | _____| | ___   _|___ /
#| '_ \| |/ _` |/ __| |/ / __| |/ / | | | |_ \
#| |_) | | (_| | (__|   <\__ \   <| |_| |___) |
#|_.__/|_|\__,_|\___|_|\_\___/_|\_\\__, |____/
#                                  |___/

#Maintainer: blacksky3 <https://github.com/blacksky3>

major=5.4.2
major_short=5.4.2
minor=50402-104
ubuntu_ver=22.04
repo_folder_ver=5.4.2

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
source=(https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-llvm/rocm-llvm_15.0.0.22506.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-cmake/rocm-cmake_0.8.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-device-libs/rocm-device-libs_1.0.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/c/comgr/comgr_2.4.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsakmt-roct-dev/hsakmt-roct-dev_20221020.0.2.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr/hsa-rocr_1.7.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/h/hsa-rocr-dev/hsa-rocr-dev_1.7.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocminfo/rocminfo_1.0.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl/rocm-opencl_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-dev/rocm-opencl-dev_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-runtime/rocm-opencl-runtime_5.4.2.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-ocl-icd/rocm-ocl-icd_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-clang-ocl/rocm-clang-ocl_0.5.0.${minor}~${ubuntu_ver}_amd64.deb)

# extracts a debian package
# $1: deb file to extract
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
  extract_debgz "${srcdir}"/rocm-llvm_15.0.0.22506.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-cmake_0.8.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-device-libs_1.0.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/comgr_2.4.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsakmt-roct-dev_20221020.0.2.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr_1.7.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/hsa-rocr-dev_1.7.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocminfo_1.0.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-dev_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-opencl-runtime_5.4.2.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-ocl-icd_2.0.0.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-clang-ocl_0.5.0.${minor}~${ubuntu_ver}_amd64.deb

  mv "${pkgdir}/opt/rocm-5.4.2/" "${pkgdir}/opt/rocm/"

  install -dm755 "${pkgdir}"/usr/share/licenses/rocm
  install -dm755 "${pkgdir}"/usr/share/doc/rocm

  # hsakmt-roct
  sed -i "s#prefix=/opt/rocm-5.4.2#prefix=/opt/rocm#g" "${pkgdir}"/opt/rocm/share/pkgconfig/libhsakmt.pc
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

sha256sums=('e6198a5fba57d33ab2d7b25aa2a96fd029af6b7af013e20c1f93d8d56744d1d0'
            '4459b56d7d6620079b42f2a7d9a7f5506a30f2534d485e9f9bc9904c4b13aeab'
            'df587fc525a34950de0457c78303a41e6640370957f07212b78d51c4ce67f5c5'
            'd7bff8a60fd3a22775c4ef63e9e5794aff32b475cb77f920f452f69ae8c74d0c'
            '358d22f52edec44adb4b10399033177dc08917680a48f8da61686d5e5cbfabd8'
            'edb93d9a3163c5a2f313c816c5581ca8ec5bec50ac6eb8fc471ce7211689801d'
            '1d1c4eb0cdb1676822921343988ac61ac2d17c49d716aa26e8870cab38d9eb4c'
            '5bf8eb892b84a49950f64c27cde862b92b711b62229ac6596ece8a71dad77853'
            'e851a7aa5c9aad793ee279aa0ccecfa7ae8bf94334eb9603d7c5712758aef4a2'
            'f2233bd0b2a521d21cb7464170b97817053533562d4ca016dca4b7a96ecff741'
            '8f805754f5d8925a98455786ad0c7b89c3ee81fd975e7107d15c7e68c42ce911'
            '18ed2c453e731cc84e87e33872b9de61138df96f205a18e9feb5991092fa6110'
            '0524840c9b6646df6ca7b4d48897b45ce1633d3932bed25418acb6ce6de022d9')
