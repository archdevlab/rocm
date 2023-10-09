#Maintainer: archdevlab <https://github.com/archdevlab>
#Credits: Carson Rueter <roachh at proton mail dot com>
#Credits: George Sofianos

major=5.7
major2=5.7.0
major_short=5.7
minor=50700-63
ubuntu_ver=22.04
repo_folder_ver=5.7

llvm_ver=17.0.0.23352
cmake_ver=0.10.0
devicelibs_ver=1.0.0
comgr_ver=2.5.0
hsakmt_ver=20230704.2.5268
hsa_ver=1.11.0
rocminfo_ver=1.0.0
rocmopencl_ver=2.0.0
rocmoclicd_ver=2.0.0
rocmclang_ver=0.5.0

pkgname=rocm-stack
pkgver=${major}
pkgrel=1
pkgdesc='ROCm OpenCL stack for Vega 10 and later products.'
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
        https://repo.radeon.com/rocm/apt/${repo_folder_ver}/pool/main/r/rocm-opencl-runtime/rocm-opencl-runtime_${major2}.${minor}~${ubuntu_ver}_amd64.deb
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
  extract_debgz "${srcdir}"/rocm-opencl-runtime_${major2}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debgz "${srcdir}"/rocm-ocl-icd_${rocmoclicd_ver}.${minor}~${ubuntu_ver}_amd64.deb
  extract_debxz "${srcdir}"/rocm-clang-ocl_${rocmclang_ver}.${minor}~${ubuntu_ver}_amd64.deb

  mv "${pkgdir}/opt/rocm-${major2}/" "${pkgdir}/opt/rocm/"

  install -dm755 "${pkgdir}"/usr/share/licenses/rocm
  install -dm755 "${pkgdir}"/usr/share/doc/rocm

  # hsakmt-roct
  sed -i "s#prefix=/opt/rocm-5.5.0#prefix=/opt/rocm#g" "${pkgdir}"/opt/rocm/share/pkgconfig/libhsakmt.pc
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

sha256sums=('fdb8e4a4f99daa25a494511687fcf542805d55fdc9ec91dd403608528ce41ea7'
            '4053b407ac31c6f466f04c1ebf1d7eef1ef6dca75eeff49d471d0bbbd1be9bf6'
            '1cb0aa477a65a6126061428ed05863421aaf7c5edb65849212e22f76a4b3ddc0'
            '611c062be7fb2746bfce25a424919cc8c6eaf3b85ff6ace63b11720413bb3052'
            '66ac1cd54b37c681b0aa4743e87cd6ddc618a1a2f5969ae61c2fac8b349e59dc'
            '987fec0426cb77fbf45a89e641ce3e16cb7e255c948691f345f918068ec58997'
            '9a226859a9bc878fa45a53f0e8e74fd9ec3bb07364f1e538019a4593fa5ecac3'
            '9e62dc35c3a1274c5a5cbff20f33ca5879d1dbd47db353e7819cb1d5f03189d8'
            '93720bed0f39af39ef80821cbfd276a8c40bd864e85ff516161be2053ce98a65'
            '576f7c7de7bb2ff68f4a6033c24c0eac233cf05751091d2b8b64a0d8a6e3f971'
            'd583a41cdedf66bddad84828f539d6dff56cdd332a0386e8fd7ef37004260c59'
            'efafdf1f51dc68799f58810e096b8132d7aa1a528b45cbe7196acbb04f2f072b'
            '8e7f50f6e7e21cba294ca647a9feec5cb5176ff41598d008f2cb66800afce010')
